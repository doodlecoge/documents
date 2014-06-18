Oracle Notes
============

create user/schema
------------------

1.  login as sysdba

        $ sqlplus / as sysdba
        SQL>

2.  create user and grant privileges

        SQL> create user <username> identified by <password>;
        SQL> grant connect, resource, create session to <username>;

3.  connect as normal user just created

        SQL> connect <username>/<password>

4.  create table and drop table

        SQL> create table tbl_test (
          2  id int not null primary key,
          3  name varchar(20) not null);

        SQL> drop table test;

create tablespace
-----------------

    $tblsp=<tablespace name>

    ${ORACLE_HOME}/bin/sqlplus system/<pass>@$ORACLE_SID << END
    create tablespace $tblsp
    datafile '$ORACLE_HOME/dbs/$tblsp.dbf'
    size 50M
    autoextend on;
    END


database views
--------------


database query
--------------

1.  Show all schemas in database

        SQL> connect / as sysdba
        SQL> select * from dba_users;

2.  Show table definition

        SELECT column_name
        FROM user_tab_cols
        WHERE table_name = 'myTableName'

    Or

        DESCRIBE name_of_table;

    For MySQL

        SHOW COLUMNS FROM table_name

3.  List Functions, Procedures, Packages

        SELECT * FROM ALL_OBJECTS
        WHERE OBJECT_TYPE IN ('FUNCTION','PROCEDURE','PACKAGE')

4.  Show procedure code

        select text from USER_SOURCE
        where name = '<YOUR PROCEDURE NAME>'
        order by line;

    **Note** that <YOUR PROCEDURE NAME> must be uppercase.



execute sql in shell using sqlplus
----------------------------------

    sqlplus "jabber/jabber@(DESCRIPTION=(ADDRESS=(PROTOCOL=TCP)
    (Host=www.example.com)(Port=1521))(CONNECT_DATA=(SID=XE)))"
    < create_table.sql