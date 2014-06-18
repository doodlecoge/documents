User Management
===============

The **useradd** command is used to add a new user, the following command line
shows the the basic usage of **useradd**.

    $ sudo useradd hch

It will crate a user named `hch` and a group with the same name, the user is
then added to the group. The **id** command can show the details of a user.

    $ id hch
    uid=501(hch) gid=501(hch) groups=501(hch)


Assign group while creating user
--------------------------------

1.  add new user to secondary group

        $ sudo groupadd dba
        $ sudo useradd -G dba hch
        $ id hch
        uid=501(hch) gid=502(hch) groups=502(hch),501(dba)

2.  add new user to primary group

        $ sudo groupadd dba
        $ sudo useradd -g dba hch
        $ id hch
        uid=501(hch) gid=501(dba) groups=501(dba)


Modify user groups
------------------

The **usermod** command is used to modify a user account.

1.  add an existing user to an existing group

        $ sudo usermod -a -G dba hch

2.  change user's primary group

        $ sudo usermod -g dba hch