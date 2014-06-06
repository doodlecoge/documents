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