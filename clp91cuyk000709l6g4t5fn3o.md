---
title: "Securing and Efficiently Managing MySQL Server Deployment in Docker: Best Practices for Database Backup and Restoration"
datePublished: Wed Nov 22 2023 00:37:59 GMT+0000 (Coordinated Universal Time)
cuid: clp91cuyk000709l6g4t5fn3o
slug: database-server
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700636684248/a6be4a7a-ecac-405e-9d39-c4bfa739c2e6.png
tags: linux, docker, mysql, databases, devops, best-practices, containers, linux-for-beginners

---

For this first, we have to set up docker on a Linux machine (Ex- AWS Instance, On-Primise, Virtual Machine, etc).

### Step-1 (Setup Docker on Virtual Machine.)

I have Rhel 9 OS with 4 GB RAM and a 2Vc Core CPU. Follow this official Docker community to set up Docker Engine in Centos: [https://docs.docker.com/engine/install/centos/](https://docs.docker.com/engine/install/centos/)

### Step-2 (Deploy MySQL container on docker.)

```plaintext
# docker info  
# docker --version
# docker images
```

Pull MySQL Image and create a volume directory for attaching with MySQL container configuration directory. Don't forget to make a mysql port 3606 entry in the firewall.

```plaintext
# mkdir -p /vol/mysql_data
# firewall-cmd --list-all
# firewall-cmd --permanent --add-port=3606/tcp 
# firewall-cmd --reload
```

```plaintext
# docker pull mysql:latest 
# docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
mysql        latest    a3b6608898d6   3 weeks ago   596MB

# mkdir -p /vol/mysql_data
```

Run MySQL container

```plaintext
# docker run -d --name=mysql_con -v /vol/mysql_data:/var/lib/mysql --restart=on-failure -e MYSQL_ROOT_PASSWORD="password" -p 3606:3606 mysql:latest

# docker ps -a 
CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS         PORTS                                                            NAMES
31ea49f88d41   mysql:latest   "docker-entrypoint.s…"   6 seconds ago   Up 5 seconds   3306/tcp, 33060/tcp, 0.0.0.0:3606->3606/tcp, :::3606->3606/tcp   mysql_con
```

Enter in MySQL Container

```plaintext
# docker exec -it 31ea49f88d41 bash
# mysql -u root -p
```

### Step-2.1 (Deploy MySQL/MariaDB on Base Machine )

```plaintext
# yum install mariadb-server mariadb -y
# systemctl start mariadb.service   &&  systemctl enable mariadb.service
# mysql_secure_installation
# mysql -u root -p
```

---

### Step-3 (Create a Database.)

Now we are going to create a new MySQL database inside MySQL container and show database.

```sql
bash-4.4# mysql --version
mysql  Ver 8.2.0 for Linux on x86_64 (MySQL Community Server - GPL)

bash-4.4# mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 8
Server version: 8.2.0 MySQL Community Server - GPL

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
```

Show how many databases have already been created in MySQL.

```sql
mysql> show databases ;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| mysql              |
| performance_schema |
| sys                |
+--------------------+
4 rows in set (0.01 sec)
```

Here only four databases are present. So first we create our database named "wordpress".

```sql
mysql> CREATE DATABASE wordpress;
Query OK, 1 row affected (0.00 sec)
```

Now we will use this newly created database, so enter it into "WORDPRESS" database. After this, we will create a table "authors" and insert some table data.

```sql
mysql> USE wordpress;
Database changed

mysql>   CREATE TABLE authors (id INT, name VARCHAR(20), email VARCHAR(20));
Query OK, 0 rows affected (0.02 sec)

mysql> INSERT INTO authors (id,name,email) VALUES(1,"Vivek","xuz@abc.com");
Query OK, 1 row affected (0.03 sec)

mysql> INSERT INTO authors (id,name,email) VALUES(2,"Priya","p@gmail.com");
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO authors (id,name,email) VALUES(3,"Tom","tom@yahoo.com");
Query OK, 1 row affected (0.00 sec)

mysql> INSERT INTO authors (id,name,email) VALUES(4,"Jerry","jerry@yahoo.com");
Query OK, 1 row affected (0.00 sec)
```

We can see we have created a new table in "wordpress" database. We can describe this table using the below MySQL query.

```sql
mysql> SHOW TABLES;
+---------------------+
| Tables_in_wordpress |
+---------------------+
| authors             |
+---------------------+
1 row in set (0.01 sec)

mysql> DESCRIBE authors;
+-------+-------------+------+-----+---------+-------+
| Field | Type        | Null | Key | Default | Extra |
+-------+-------------+------+-----+---------+-------+
| id    | int         | YES  |     | NULL    |       |
| name  | varchar(20) | YES  |     | NULL    |       |
| email | varchar(20) | YES  |     | NULL    |       |
+-------+-------------+------+-----+---------+-------+
3 rows in set (0.00 sec)
```

As we can see inserted table data, there are four records in this table.

```sql
mysql> SELECT * FROM authors;
+------+-------+-----------------+
| id   | name  | email           |
+------+-------+-----------------+
|    1 | Vivek | xuz@abc.com     |
|    2 | Priya | p@gmail.com     |
|    3 | Tom   | tom@yahoo.com   |
|    4 | Jerry | jerry@yahoo.com |
+------+-------+-----------------+
4 rows in set (0.00 sec)
```

### Step-3.1 (User Create and grant permission to access database)

Creating a new user "rakesh" and assigned password to access the database from localhost `'rakesh'@'localhost'`.

```sql
mysql> CREATE USER 'rakesh'@'localhost' IDENTIFIED BY 'password';
Query OK, 0 rows affected (0.02 sec)
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><code>Note 3.1.1:</code> If you want to access the database from anywhere by user "rakesh".</div>
</div>

```sql
mysql> CREATE USER 'rakesh'@'%' IDENTIFIED BY 'password';
Query OK, 0 rows affected (0.02 sec)
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><code>Note 3.1.2:</code> In Case to drop a created user.</div>
</div>

```sql
mysql> DROP USER 'rakesh'@'%';
Query OK, 0 rows affected (0.05 sec)

mysql> DROP USER 'rakesh'@'localhost';
Query OK, 0 rows affected (0.05 sec)
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><code>Note 3.1.3:</code> Grant access authorization on specific database and there all tables at once. and access through the localhost server (Where the actual mysql server is running).</div>
</div>

```sql
mysql> GRANT ALL PRIVILEGES ON WORDPRESS.* TO 'rakesh'@'localhost' WITH GRANT OPTION;
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> FLUSH PRIVILEGES;
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><code>Note 3.1.4:</code> If you want to give authorization access to all databases and their tables <code>*.*</code> at once, and access from anywhere using user rakesh <code>'rakesh'@'%'.</code> You can try this.</div>
</div>

```sql
mysql> GRANT ALL PRIVILEGES ON *.* TO 'rakesh'@'%' WITH GRANT OPTION;
Query OK, 0 rows affected, 1 warning (0.00 sec)

mysql> FLUSH PRIVILEGES;
```

If you want to check, which database is assigned to which user .

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><code>Note 3.1.5: </code>There is a special pre-configured database named "mysql" inside MySQL. That has overall databases user credentials and much more information. Here You can check "rakesh" user is authorized to access the "WORDPRESS" database.</div>
</div>

```sql
mysql> show databases;
mysql> use mysql;
mysql> show tables;
mysql> select Host, User from user;
+-----------+------------------+
| Host      | User             |
+-----------+------------------+
| %         | root             |
| localhost | mysql.infoschema |
| localhost | mysql.session    |
| localhost | mysql.sys        |
| localhost | root             |
| localhost | rakesh           |
+-----------+------------------+
6 rows in set (0.00 sec)
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><code>Note 3.1.6: </code>Login with new user rakesh and check whether this is authenticated and authorized to access the database from localhost.</div>
</div>

```sql
bash-4.4# mysql -u rakesh -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 12
Server version: 8.2.0 MySQL Community Server - GPL

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| performance_schema |
| wordpress          |
+--------------------+
3 rows in set (0.00 sec)

mysql> use wordpress;
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> show tables;
+---------------------+
| Tables_in_wordpress |
+---------------------+
| authors             |
+---------------------+
1 row in set (0.00 sec)

mysql> select * from authors;
+------+-------+-----------------+
| id   | name  | email           |
+------+-------+-----------------+
|    1 | Vivek | xuz@abc.com     |
|    2 | Priya | p@gmail.com     |
|    3 | Tom   | tom@yahoo.com   |
|    4 | Jerry | jerry@yahoo.com |
+------+-------+-----------------+
4 rows in set (0.00 sec)
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><code>Note 3.1.7: </code>If you faced such error to access using user rakesh "ERROR 1045 (28000): Access denied for user 'root'@'<a target="_blank" rel="noopener noreferrer nofollow" href="http://localhost" style="pointer-events: none">localhost</a>' (using password: YES)"</div>
</div>

```plaintext
bash-4.4# mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
bash-4.4#
--------- Make entry of container_ip with localhost in hosts file
bash-4.4# cat /etc/hosts
bash-4.4# echo "<container_ip>    localhost" >> /etc/hosts
--------- Now try with same login 
bash-4.4# mysql -u rakesh -p
Enter password:
```

---

### Step-4 (Create a backup of MySQL database.)

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><code>Note 4.1:</code> Make sure you are not inside of any database, and you are on a container shell, and you give enough privileges to your user to take backup. check notes point: <a target="_blank" rel="noopener noreferrer nofollow" href="" style="pointer-events: none"><code>Note: 3.1.4</code></a></div>
</div>

```plaintext
bash-4.4# mysqldump -u rakesh -p wordpress > /var/lib/mysql/mysql_backup.sql
Enter password:
bash-4.4# ls -l /var/lib/mysql
total 100712
-rw-r-----. 1 mysql mysql   196608 Nov 22 04:33 '#ib_16384_0.dblwr'
-rw-r-----. 1 mysql mysql  8585216 Nov 21 12:31 '#ib_16384_1.dblwr'
drwxr-x---. 2 mysql mysql     4096 Nov 22 03:51 '#innodb_redo'
drwxr-x---. 2 mysql mysql      187 Nov 22 03:51 '#innodb_temp'
-rw-r-----. 1 mysql mysql       56 Nov 21 12:31  auto.cnf
-rw-r-----. 1 mysql mysql  3039831 Nov 21 12:31  binlog.000001
-rw-r-----. 1 mysql mysql     2977 Nov 21 13:43  binlog.000002
-rw-r-----. 1 mysql mysql     2860 Nov 22 04:33  binlog.000003
-rw-r-----. 1 mysql mysql       48 Nov 22 03:51  binlog.index
-rw-------. 1 mysql mysql     1680 Nov 21 12:31  ca-key.pem
-rw-r--r--. 1 mysql mysql     1108 Nov 21 12:31  ca.pem
-rw-r--r--. 1 mysql mysql     1108 Nov 21 12:31  client-cert.pem
-rw-------. 1 mysql mysql     1676 Nov 21 12:31  client-key.pem
-rw-r-----. 1 mysql mysql     4317 Nov 21 13:43  ib_buffer_pool
-rw-r-----. 1 mysql mysql 12582912 Nov 22 04:33  ibdata1
-rw-r-----. 1 mysql mysql 12582912 Nov 22 03:51  ibtmp1
drwxr-x---. 2 mysql mysql      143 Nov 21 12:31  mysql
-rw-r-----. 1 mysql mysql 32505856 Nov 22 04:33  mysql.ibd
lrwxrwxrwx. 1 mysql mysql       27 Nov 22 03:51  mysql.sock -> /var/run/mysqld/mysqld.sock
-rw-r--r--. 1 root  root      2007 Nov 22 04:54  mysql_backup.sql
drwxr-x---. 2 mysql mysql     8192 Nov 21 12:31  performance_schema
-rw-------. 1 mysql mysql     1680 Nov 21 12:31  private_key.pem
-rw-r--r--. 1 mysql mysql      452 Nov 21 12:31  public_key.pem
-rw-r--r--. 1 mysql mysql     1108 Nov 21 12:31  server-cert.pem
-rw-------. 1 mysql mysql     1676 Nov 21 12:31  server-key.pem
drwxr-x---. 2 mysql mysql       28 Nov 21 12:31  sys
-rw-r-----. 1 mysql mysql 16777216 Nov 22 04:33  undo_001
-rw-r-----. 1 mysql mysql 16777216 Nov 22 04:32  undo_002
drwxr-x---. 2 mysql mysql       25 Nov 22 04:30  wordpress
bash-4.4# cat /var/lib/mysql/mysql_backup.sql
```

### Step-4.1 (Create recursive backup automatically and send it onto a different server using rsync.)

The backup of the WordPress database was created from a Docker container named `mysql_con`, using the user named `rakesh`. This backup was stored at the location `/var/lib/mysql`. This location is where MySQL stores various types of configuration files and important data.

Additionally, this specific location (`/var/lib/mysql`) is connected to a directory in the BaseOS system named `/vol/mysql_data`. This connection was established when we attached it using the `-v` option in Docker. So we will create a cronjob with user rakesh on BaseOS, where docker is running. (or you can create a cronjob inside the docker container as well)

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><code>Note 4.1.1:</code> If you are working on a docker mysql container, try this.</div>
</div>

If you are working on a docker container. Create a .my.cnf file inside your docker mysql\_con container with the following configuration `(Then you don't need to reveal your username and password each time).`

```plaintext
bash-4.4# vi ~/.my.cnf

[client]
user=username
password=yourpass

:wq!
```

Then come to BaseOS, and create a script file.

```plaintext
[root@localhost ~]# vi /root/script.sh
#!/bin/bash

mysqldump wordpress > /var/lib/mysql/mysql_backup.sql

:wq!
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Then create a crontab file to schedule cronjob to take backup every 15 minutes.</div>
</div>

```plaintext
[root@localhost ~]# crontab -e  -u  root 
*/15    *       *       *       *       docker exec mysql_con /bin/bash /root/script.sh   
*/16    *       *       *       *       rsync -avz /var/lib/mysql/mysql_backup.sql /root/mysql_backup
```

Don't forgot to restart crond service for crontab jobs.

```plaintext
oot@localhost ~]# systemctl restart crond
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Note: You can check updated backup and there timestamp</div>
</div>

```plaintext
[root@localhost mysql_data]# ls -al /root/mysql_backup
total 8
drwxr-xr-x.  2 root root   30 Nov 22 11:53 .
dr-xr-x---. 15 root root 4096 Nov 22 11:55 ..
-rw-r--r--.  1 root root 1273 Nov 22 11:13 mysql_backup.sql
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Note: If you want to send a backup from the MySQL Host Server to another server, you can set "rsync" between two different servers.</div>
</div>

---

### Step-5 (Restore backup of MySQL database.)

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Make sure you are on container bash, not inside the MySQL database.</div>
</div>

```plaintext
bash-4.4#  mysql wordpress < /var/lib/mysql/mysql_backup.sql
```

---

---

### Some MySQL Interview Questions :

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Here we will discuss some most important MySQL-related questions.</div>
</div>

`Question-1` How to reset MySQL root password?

> `Step-1:` Suppose your MySQL database server is running on local machine. So first stop the MySQL server service.
> 
> ```plaintext
> [root@localhost ~]# systemctl status mysql
> [root@localhost ~]# systemctl stop mysql
> ```
> 
> `Step-2:` Find mysqld process id and kill it using `kill -9 pid_mysqld` or `kill -19 pid_mysqld.`
> 
> ```sql
> [root@localhost ~]# top
> [root@localhost ~]# kill -9 25691
> [root@localhost ~]# kill -19 25691
> 
> ----------- Check using top command, whether it is mysqld process is still running or not
> [root@localhost ~]# top
> ```
> 
> `Step-3:` Run mysql in safe mode

---

`Question-2` What is the main difference between DROP, DELETE & TRUNCATE commands in MySQL Query?

> Suppose You have a database "earth" and there is some table inside it like "continents, oceans, animals, humans, birds". Now you want to remove some records from the database, tables, records & databases etc. These things can be implemented by DROP, DELETE, and TRUNCATE Query commands.
> 
> * DROP = Data + Structure of Table will be removed. (Ex: complete Table, Database).
>     
>     ```sql
>     DROP table <table_name>;
>     DROP database <database_name>;
>     ```
>     
> * DELETE = Only the data part will be removed and no sequence will be changed for the next record. (No counter will be reset. (Ex- <s>1,2,3,4,5 </s> ) and then (6,7,8,9,10 ...)
>     
>     ```sql
>     DELETE FROM table_name WHERE condition;
>     ```
>     
> * TRUNCATE = All rows/records will be deleted (remove) and sequence (Counter) will be reset. (Ex- <s>1,2,3,4,5 </s> ) and then (1,2,3,4,5,6,7 ...)
>     
>     ```sql
>     TRUNCATE table <table_name>;
>     ```
>     

---

`Question-3` How to assign "CREATE, ALTER, DROP, INSERT, UPDATE, DELETE and SELECT " grant permissions to a user Rakesh on wordpress database, which can access the database from localhost and anywhere?

> `Note-3.1:` First, if you don't have any users, you create the user and then grant the permissions. To `GRANT ALL` privileges to a `user`, allowing that user full control over a specific `database`, use the following syntax:
> 
> ```sql
> mysql> CREATE USER 'Rakesh'@'%' IDENTIFIED BY 'password';
> Query OK, 0 rows affected (0.02 sec)
> 
> ------------------------------------------------------------
> mysql> GRANT ALL PRIVILEGES ON wordpress.* TO 'Rakesh'@'%';
> Query OK, 0 rows affected (0.02 sec)
> 
> mysql> GRANT ALL PRIVILEGES ON wordpress.table_name TO 'Rakesh'@'localhost';
> Query OK, 0 rows affected (0.02 sec)
> ```
> 
> `Note-3.2:` Specific Grant permissions to user Rakesh on database wordpress to access from localhost and anywhere.
> 
> ```sql
> mysql> GRANT CREATE, ALTER, DROP, INSERT, UPDATE, DELETE, SELECT, REFERENCES, RELOAD on wordpress.* TO 'Rakesh'@'%' WITH GRANT OPTION;  
> Query OK, 0 rows affected (0.02 sec)
> 
> 
> mysql> GRANT CREATE, ALTER, DROP, INSERT, UPDATE, DELETE, SELECT, REFERENCES, RELOAD on wordpress.table_name TO 'Rakesh'@'localhost' WITH GRANT OPTION;  
> Query OK, 0 rows affected (0.02 sec)
> ```

---

`Question-4` We have two users Rakesh & Anjali, and Two databases College & School as well. Now how will you Assign the College database to access user Anjali with specific IP 192.175.23.10, and the School database with user Rakesh with access from anywhere?

> ```sql
> mysql> GRANT ALL PRIVILEGES ON
>     -> College.* TO 'Anjali'@'192.175.23.10'
>     -> WITH GRANT OPTION;
> Query OK, 0 rows affected (0.00 sec)
> 
> ---------------------------------------------------------------------------
> mysql> GRANT ALL PRIVILEGES ON
>     -> School.* TO 'Rakesh'@'%'
>     -> WITH GRANT OPTION;
> Query OK, 0 rows affected (0.01 sec)
> 
> ---------------------------------------------------------------------------
> mysql> USE mysql;
> Database changed
> mysql> SELECT User, Host
>     -> FROM user;
> 
> +------------------+------------+
> | User             | Host       |
> +------------------+------------+
> | Anjali           | 172.17.0.2 |
> | Rakesh           | %          |
> | root             | %          |
> | mysql.infoschema | localhost  |
> | mysql.session    | localhost  |
> | mysql.sys        | localhost  |
> | root             | localhost  |
> +------------------+------------+
> 7 rows in set (0.00 sec)
> ---------------------------------------------------------------------------
> bash-4.4# mysql -u Rakesh -p
> Enter password:
> mysql> show databases;
> +--------------------+
> | Database           |
> +--------------------+
> | School             |
> | information_schema |
> | performance_schema |
> +--------------------+
> 3 rows in set (0.01 sec)
> ---------------------------------------------------------------------------
> bash-4.4# mysql -u Anjali -p -h 172.17.0.2
> Enter password:
> mysql> show databases;
> +--------------------+
> | Database           |
> +--------------------+
> | College            |
> | information_schema |
> | performance_schema |
> +--------------------+
> 3 rows in set (0.01 sec)
> ```

---

`Question-5` How we can know user (Ex:- Rakesh) access on a specific host?

> There is a pre-existing 'mysql' database within the MySQL server, specifically designed to store all the system's internal configurations, user accounts, privileges, and other crucial system-related information.
> 
> ```sql
> bash-4.4# mysql -u root -p
> Enter password:
> 
> ----------------------------------------------------------------------
> mysql> SHOW DATABASES;
> +--------------------+
> | Database           |
> +--------------------+
> | information_schema |
> | mysql              |
> | performance_schema |
> | sys                |
> | wordpress          |
> +--------------------+
> 5 rows in set (0.02 sec)
> 
> ----------------------------------------------------------------------
> mysql> USE mysql;
> Reading table information for completion of table and column names
> You can turn off this feature to get a quicker startup with -A
> Database changed
> 
> ----------------------------------------------------------------------
> mysql> mysql> show tables;
> +------------------------------------------------------+
> | Tables_in_mysql                                      |
> +------------------------------------------------------+
> | columns_priv                                         |
> | component                                            |
> | db                                                   |
> | default_roles                                        |
> | engine_cost                                          |
> | func                                                 |
> | general_log                                          |
> | global_grants                                        |
> | gtid_executed                                        |
> | help_category                                        |
> | help_keyword                                         |
> | help_relation                                        |
> | help_topic                                           |
> | innodb_index_stats                                   |
> | innodb_table_stats                                   |
> | ndb_binlog_index                                     |
> | password_history                                     |
> | plugin                                               |
> | procs_priv                                           |
> | proxies_priv                                         |
> | replication_asynchronous_connection_failover         |
> | replication_asynchronous_connection_failover_managed |
> | replication_group_configuration_version              |
> | replication_group_member_actions                     |
> | role_edges                                           |
> | server_cost                                          |
> | servers                                              |
> | slave_master_info                                    |
> | slave_relay_log_info                                 |
> | slave_worker_info                                    |
> | slow_log                                             |
> | tables_priv                                          |
> | time_zone                                            |
> | time_zone_leap_second                                |
> | time_zone_name                                       |
> | time_zone_transition                                 |
> | time_zone_transition_type                            |
> | user                                                 |
> +------------------------------------------------------+
> 38 rows in set (0.00 sec)
> 
> ----------------------------------------------------------------------
> mysql> SELECT User, Host from user;
> +------------------+-----------+
> | User             | Host      |
> +------------------+-----------+
> | root             | %         |
> | mysql.infoschema | localhost |
> | mysql.session    | localhost |
> | mysql.sys        | localhost |
> | rakesh           | localhost |
> | root             | localhost |
> +------------------+-----------+
> 6 rows in set (0.00 sec)
> 
> mysql>
> ```

`Question-6` How to remove a user from the MySQL database?

> To remove a user from the database, you have to be login from root login.
> 
> ```sql
> bash-4.4# mysql -u root -p
> Enter password:
> ----------------------------------------------------------------------
> mysql> select User, Host from user;
> +------------------+------------+
> | User             | Host       |
> +------------------+------------+
> | Anjali           | %          |
> | Rakesh           | %          |
> | root             | %          |
> | Sita             | 172.17.0.2 |
> | mysql.infoschema | localhost  |
> | mysql.session    | localhost  |
> | mysql.sys        | localhost  |
> | root             | localhost  |
> +------------------+------------+
> 8 rows in set (0.00 sec)
> ----------------------------------------------------------------------
> mysql> DROP USER 'Rakesh'@'%';
> Query OK, 0 rows affected (0.01 sec)
> ```

---

`Question-7` What is the use of "FLUSH PRIVILEGES" command in MySQL database?

> Executing `FLUSH PRIVILEGES` tells the MySQL server to discard the current in-memory privileges and reload the grant tables, ensuring that any recent modifications to user privileges or access rights take effect immediately without requiring a server restart.
> 
> It's important to note that in modern versions of MySQL, many privilege-related changes automatically take effect without explicitly running `FLUSH PRIVILEGES`. However, there are specific scenarios where executing this command might be necessary to ensure immediate application of privilege changes, especially after directly modifying the grant tables.

---

`Question-8` Give Anjali user grant permission to access only the oceans table in the earth database.

> ```sql
> mysql> GRANT ALL PRIVILEGES ON
>     -> earth.oceans TO 'Anjali'@'%'
>     -> WITH GRANT OPTION;
> Query OK, 0 rows affected (0.01 sec)
> ```

`Question-9` What is the format to write date datatype in MySQL & Oracle?

> In Oracle : DD-MM-YYYY
> 
> In MySQL: YYYY-MM-DD

---

### References:

* `Docker setup on centos:` [https://docs.docker.com/engine/install/centos/](https://docs.docker.com/engine/install/centos/)
    
* `Create database, and tables and insert the data:` [https://www.w3schools.com/sql/sql\_create\_table.asp](https://www.w3schools.com/sql/sql_create_table.asp)
    
* `Create user and grant permissions:` [https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)
    
* `How to Use the Rsync Utility to Make a Remote Backup of a Linux System:` [https://jumpcloud.com/blog/how-to-use-rsync-remote-backup-linux-system#:~:text=By%20default%2C%20rsync%20does%20not,times%20using%20a%20cron%20job](https://jumpcloud.com/blog/how-to-use-rsync-remote-backup-linux-system#:~:text=By%20default%2C%20rsync%20does%20not,times%20using%20a%20cron%20job).
    
* `Hide your credentials publically during the crontab task:` [https://stackoverflow.com/questions/62287061/connect-to-2-instances-of-mysql-with-no-password-interaction-using-command-line#:~:text=Do%20chmod%20600%20~%2F.,like%20user%20can%20see%20it.&text=That%20allows%20you%20to%20just%20type%20mysql%20and%20log%20on](https://stackoverflow.com/questions/62287061/connect-to-2-instances-of-mysql-with-no-password-interaction-using-command-line#:~:text=Do%20chmod%20600%20~%2F.,like%20user%20can%20see%20it.&text=That%20allows%20you%20to%20just%20type%20mysql%20and%20log%20on).