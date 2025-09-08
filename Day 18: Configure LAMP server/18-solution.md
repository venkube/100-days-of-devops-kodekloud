## Configure LAMP Server
### Install apache, php and its dependecies on app servers
```
yum install php httpd php-mysqlnd -y
```

### Enable and start apache and php
```
systemctl start httpd; systemctl enable httpd
systemctl enable php-fpm;systemctl start php-fpm
```

### Install mariadb on DB server
```
yum install mariadb-server
systemctl start mariadb
systemctl enable mariadb
```

### Create DB user and a database
```
Create a database named kodekloud_db7 and create a database user named kodekloud_joy identified as password BruCStnMT5. Further make sure this newly created user is able to perform all operation on the database you created.

# mariadb -u root -p
Enter password: 
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 3
Server version: 10.5.27-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]> CREATE DATABASE kodekloud_db7;
Query OK, 1 row affected (0.000 sec)

MariaDB [(none)]> CREATE USER kodekloud_joy IDENTIFIED BY 'BruCStnMT5';
Query OK, 0 rows affected (0.008 sec)

MariaDB [(none)]> GRANT ALL PRIVILEGES ON kodekloud_db7.* TO 'kodekloud_joy';
Query OK, 0 rows affected (0.002 sec)

MariaDB [(none)]> CREATE USER 'kodekloud_joy'@'localhost' IDENTIFIED BY 'BruCStnMT5';
Query OK, 0 rows affected (0.001 sec)

MariaDB [(none)]> GRANT ALL PRIVILEGES ON your_database.* TO 'kodekloud_joy'@'localhost';
Query OK, 0 rows affected (0.006 sec)

MariaDB [(none)]> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.006 sec)

MariaDB [(none)]> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| kodekloud_db7      |
| mysql              |
| performance_schema |
+--------------------+
4 rows in set (0.007 sec)

MariaDB [(none)]> SELECT User, Host FROM mysql.user;
+---------------+-----------+
| User          | Host      |
+---------------+-----------+
| kodekloud_joy | %         |
| kodekloud_joy | localhost |
| mariadb.sys   | localhost |
| mysql         | localhost |
| root          | localhost |
+---------------+-----------+
5 rows in set (0.008 sec)

MariaDB [(none)]> SELECT User, Host FROM mysql.user^C


+---------------+-----------+
| User          | Host      |
+---------------+-----------+
| kodekloud_joy | %         |
| kodekloud_joy | localhost |
| mariadb.sys   | localhost |
| mysql         | localhost |
| root          | localhost |
+---------------+-----------+
5 rows in set (0.001 sec)

```

### validate manually by routing to the path /var/www/html and execute php command
```
root@stapp01 html]# php index.php
App is able to connect to the database using user kodekloud_joy
```
