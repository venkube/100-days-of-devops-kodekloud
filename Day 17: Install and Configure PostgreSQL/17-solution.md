## Install Postges sql and Configure it

#### To check postgres is running and installed
```
# psql --version
psql (PostgreSQL) 13.14

# systemctl status postgresql
```

### Access the postgresql cli prompt
```
# sudo -u postgres psql
could not change directory to "/home/peter": Permission denied
psql (13.14)
Type "help" for help.

postgres=# 
```

### Create the Postgres sql user with password
```
postgres=# CREATE USER kodekloud_cap WITH PASSWORD 'ksH85UJjhb';
CREATE ROLE

```

### To list the users
```
postgres=# \du
                                     List of roles
   Role name   |                         Attributes                         | Member of 
---------------+------------------------------------------------------------+-----------
 kodekloud_cap |                                                            | {}
 postgres      | Superuser, Create role, Create DB, Replication, Bypass RLS | {}
```

### To create database
```
postgres=# CREATE DATABASE  kodekloud_db4 WITh OWNER=kodekloud_cap;
CREATE DATABASE
```

### Grant full access
```
kodekloud_db4=# GRANT ALL PRIVILEGES ON ALL TABLES IN SCHEMA public TO kodekloud_cap;
GRANT
kodekloud_db4=# GRANT ALL PRIVILEGES ON ALL SEQUENCES IN SCHEMA public TO  kodekloud_cap;
GRANT
kodekloud_db4=# GRANT ALL PRIVILEGES ON ALL FUNCTIONS IN SCHEMA public TO  kodekloud_cap;
GRANT
kodekloud_db4=# \l
                                       List of databases
     Name      |     Owner     | Encoding  | Collate | Ctype |        Access privileges        
---------------+---------------+-----------+---------+-------+---------------------------------
 kodekloud_db4 | kodekloud_cap | SQL_ASCII | C       | C     | =Tc/kodekloud_cap              +
               |               |           |         |       | kodekloud_cap=CTc/kodekloud_cap
 postgres      | postgres      | SQL_ASCII | C       | C     | 
 template0     | postgres      | SQL_ASCII | C       | C     | =c/postgres                    +
               |               |           |         |       | postgres=CTc/postgres
 template1     | postgres      | SQL_ASCII | C       | C     | =c/postgres                    +
               |               |           |         |       | postgres=CTc/postgres
 ```

