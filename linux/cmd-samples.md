cut
===


1.  select column of character

        $ echo 0123456789 | cut -c2
        1

2.  select range of columns

        $ echo 0123456789 | cut -c1-3
        012

        $ echo 0123456789 | cut -c3-
        23456789

        $ echo 0123456789 | cut -c-8
        01234567

        $ echo 0123456789 | cut -c-
        0123456789

3.  select a specific field

        $ echo "the quick brown fox" | cut -d' ' -f2
        quick

4.  select multiple fields

        $ echo "the quick brown fox" | cut -d' ' -f2,4
        quick fox

        $ echo "the quick brown fox" | cut -d' ' -f2-4
        quick brown fox

        $ echo "the quick brown fox" | cut -d' ' -f2-4,1
        the quick brown fox

5.  select fields only when contains delimiter

        $ echo "the-quick-brown-fox" | cut -d' ' -f1000
        the-quick-brown-fox

        $ echo "the-quick-brown-fox" | cut -d' ' -s -f1
        <no output>

6.  select columns expect the specified fields

        $ echo "the quick brown fox" | cut -d' ' --complement -f2
        the brown fox

7.  change output delimiter for display

        $ echo "the quick brown fox" | cut -d' ' -f1- --output-delimiter=-
        the-quick-brown-fox

8.  change output delimiter to new-line

        $ echo "the quick brown fox" | cut -d' ' -f1- --output-delimiter=$'\n'
        the
        quick
        brown
        fox



$ sign in terminal
------------------

`$`usually means expand. You can expand `$variable` content, `$(command)`
output or `$((arithmetic))` result.

    $ echo $JAVA_HOME
    <path to your java home dir>

    $ echo $(ls)
    <list files/folders under current folder>

    $ echo $((1+2-3*4/5))
    1

`$'string'` is used to extend backslash character

    $ echo $'line-1\nline-2'
    line-1
    line-2

`$[...]` is an obsolete, deprecated syntax used for math.

    $ echo $[1+1]
    2


xargs
-----

**xargs** read items from the standard input, delimited by blanks or new lines,
and pass it to the command. Blank lines in the standard input are ignored.
Items are passed to the command all at once unless the `-n` option is given.
File names containing blanks and/or newlines can not be handled correctly by
**xargs**. In these situations, it's better to use `-0` option which consider
`null character` as the item separator. When using this option you will need
to ensure the program which produces the input for **xargs** also use `null
character` as separator.



The following example will print `1 2 3 4 5` (echo is the default command)

    $ echo 1 2 3 4 5 | xargs echo
    1 2 3 4 5

or

    $ echo 1 2 3 4 5 | xargs
    1 2 3 4 5

The above example pass all the 5 items at once to **xargs** command. You can
limit the number of arguments passed to **xargs** each time by using `-n`
option. Following will print two lines.

    $ echo 1 2 3 4 5 | xargs -n 3
    1 2 3
    4 5

When the command takes more than 2 arguments, you can use `-I` option to set
placeholder for the command which will be replaced by input items. Bellow is
not a proper example, however, it's sufficient to demonstrates the usage.

    $ $ echo 1 2 3 4 5 | xargs -I{} echo {} 6
    1 2 3 4 5 6


sed
---

Sed has several commands, but **substitution** command: `s` is most used, it
takes the form `sed s/regular-expression/new-value/`. The substitution
command will replace the portion of text, matched by *regular expression*,
with the new value.

    $ echo a brown fox | sed s/brown/yellow/
    a yellow fox

If the regular expression matches multiple places of a line, only the first one
is replaced with new value, see the following example.

    $ echo $'1 2 3 2 1\n3 2 1 2 3' | sed s/2/TWO/
    1 TWO 3 2 1
    3 TWO 1 2 3






TO BE ADDED
===========

    awk
    tcpdump
    sort
    svn
    git
    diff/quilt
    tr
