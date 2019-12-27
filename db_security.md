# Database Security
## __MySQL Security__

__Configuration__
1. Drop the Test database
    ```
    MariaDB [(none)]> SHOW GRANTS\G
    MariaDB [(none)]> USE test;
    MariaDB [test]> CREATE TABLE testtable (a INT);
    MariaDB [test]> INSERT INTO testtable VALUES (1), (2), (3);
    MariaDB [test]> SELECT * FROM testtable;
    ```
1. Remove all anonymous accounts
1. Remove Users Without Password
    ```
    > select user, host, password from mysql.user where user like '';
    > SHOW GRANTS;
    ```
1. Change default port mappings
1. Alter which hosts have access to MySQL
1. Do not run MySQL with root level privileges
1. Remove and disable the MySQL history file
1. Disable remote logins

   make sure that every user can connect to MySQL only from specific hosts. You can always define several entries for the same user (myuser@host1, myuser@host2), this should help to reduce a need for wildcards (myuser@’%’).

1. Limit or disable SHOW DATABASES
1. Disable the use of LOAD DATA LOCAL INFILE command
1. Obfuscate the root account
1. Set the proper file permissions

__User Management__
1. 'user_name'@'host_name'
   ```
   'tim'@'host01.myhost.com'
   'hd'@'192.168.2.%'
   'root'@'%.host.com'
   ```
1. To create user
   ```
   > CREATE USER 'bill'@'localhost' IDENTIFIED BY 'Pa$$w0rd';
   > CREATE USER 'ash'@'%.host.com' IDENTIFIED BY 'Pa$$w0rd';
   CREATE USER ''@'192.168.56.10'  
   > GRANT SELECT on mydb.* to 'tim'@'localhost' IDENTIFIED BY 'password';
   > GRANT SELECT,UPDATE, INSERT, DEETE  on mydb.student to 'tim'@'localhost' IDENTIFIED BY 'password';
   ```
1. More on GRANT
   ```
   > SHOW GRANTS;
   > SHOW GRANTS FOR tim@localhsot;
   > REVOKE INSERT on on mydb.student to 'tim'@'localhost'
   > REVOKE INSERT on on mydb.student to 'tim'@'localhost'
   ```
   Grant tables from mysql
   - user
   - db
   - table_priv
   - columns_priv
   - procs_priv
   
more in for [here](https://www.youtube.com/watch?v=67wBO_7Vadc)

อยากเชี่ยวชาญ MySQL ดูนี้ [More Mysql](https://youtu.be/E0CNTcfteTU)