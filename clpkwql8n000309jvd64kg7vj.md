---
title: "Docker Containerization MySQL + WordPress web installation on cloud AWS"
datePublished: Thu Nov 30 2023 08:01:56 GMT+0000 (Coordinated Universal Time)
cuid: clpkwql8n000309jvd64kg7vj
slug: docker-containerization-mysql-wordpress-web-installation-on-cloud-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701331133242/a1e7ec0d-1605-4248-af84-0c5444cb90ee.png
tags: ec2, linux, docker, aws, wordpress, mysql, server, projects, beginner, devops, containers

---

---

## Step-1 (Install Docker Engine in your Base Machine)

I am using here AWS Cloud infrastructure :

* Ubuntu OS
    
* T2.Medium Ec2 Instance
    
* MobaXterm (ssh through Windows)
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701330875286/8f6d9097-ca79-40f9-9656-6e5f9515fb60.png align="center")

---

### Step-2 ( Run MySQL container)

First of all we have to require to run MySQL container with some Environment variable using `option -e` like

* \-e MYSQL\_ROOT\_PASSWORD=
    
* \-e MYSQL\_DATABASE=
    

```sql
# docker info
# docker --version

# docker pull mysql:latest
# docker pull wordpress:latest
# docker images
# docker run -d --name=mysql -e MYSQL_ROOT_PASSWORD=password -e MYSQL_DATABASE=wordpress mysql 
# docker ps -a
# docker inspect mysql
```

```sql
root@wordpress:~# docker images
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
wordpress    latest    bc823df9ead2   8 days ago    668MB
mysql        latest    a3b6608898d6   5 weeks ago   596MB
```

```sql
root@wordpress:~# docker ps -a
CONTAINER ID   IMAGE       COMMAND                  CREATED          STATUS          PORTS                                   NAMES
a7f96e8a976c   mysql       "docker-entrypoint.s…"   23 minutes ago   Up 23 minutes   3306/tcp, 33060/tcp        mysql
```

Check MySQL container working and database has been created or not, so come into MySQL container using option `docker exec -it mysql bash` and check mysql database

```sql
root@wordpress:~# docker exec -it mysql bash
bash-4.4# mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 37
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
| mysql              |
| performance_schema |
| sys                |
| wordpress          |
+--------------------+
5 rows in set (0.00 sec)
```

---

### Step-3 ( Run WordPress container )

Now its time to launch WordPress container with some important environment variables like MySQL container image and some port information. We also can assign volume with docker containers. So lets launch wordpress container, and don't forgot to assign link between MySQL and Wordpress container.

```sql
docker run -d --name=wordpress --link=mysql 
-p 8081:80 \
-e WORDPRESS_DB_HOST=mysql_container_IP:3306 \
-e WORDPRESS_DB_USER=root \
-e WORDPRESS_DB_PASSWORD=grras \
-e WORDPRESS_DB_NAME=wordpress \
-e WORDPRESS_TABLE_PREFIX=wp_ 
-v wordpress_vol:/var/www/html -d wordpress
```

Lets check the wordpress and mysql container status

```sql
root@wordpress:~# docker ps -a
CONTAINER ID   IMAGE       COMMAND                  CREATED          STATUS          PORTS                                   NAMES
806e196f544f   wordpress   "docker-entrypoint.s…"   32 minutes ago   Up 32 minutes   0.0.0.0:8081->80/tcp, :::8081->80/tcp   wordpress
a7f96e8a976c   mysql       "docker-entrypoint.s…"   34 minutes ago   Up 34 minutes   3306/tcp, 33060/tcp                     mysql
root@wordpress:~#
```

Congratulations your both containers are working fine and showing up status. Thats good. Let's explore wordpress site using `http://Host_Machine_IP:3306` . we will take machines' public ip from the AWS instances dashboard.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701330188045/5a9c7075-223f-4c46-9001-63bdfaecf580.png align="center")

---

### Step-4 ( Browse WordPress + MySQL website using the browser )

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701330256211/c2283921-2844-4bf6-8e57-6dc0bee744e8.png align="center")

---

### Step-5 (Port forwarding or Port redirection)