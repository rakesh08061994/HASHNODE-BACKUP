---
title: "Relational Database Server implementation on Rhel Linux-9"
datePublished: Fri Jan 19 2024 12:10:49 GMT+0000 (Coordinated Universal Time)
cuid: clrkln93h000708ju7ckzamm6
slug: relational-database-server-implementation-on-rhel-linux-9
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705684219961/48ff02e0-367c-45dd-831d-756aa17757aa.png
tags: interview, linux, mysql, databases, beginner, devops, serverless, articles, relational-database, linux-for-beginners, mysqldump, linux-basics, devops-articles, devops-journey, rakamodify

---

---

# Introduction:

MySQL is like a big, digital filing cabinet where you can store, organize, and retrieve your data. It’s important because it’s fast, reliable, and easy to use. It’s different from other databases because it’s open-source, which means anyone can use or modify it for free. It uses a language called SQL to manage the data, which is widely used and powerful. It’s like the grammar rules for talking to the database. MySQL is also good at handling lots of data and can be used by big websites or apps. It’s a popular choice for web development because it can work well with various programming languages and tools. It’s also part of the popular LAMP stack for web development, which stands for Linux, Apache, MySQL, and PHP.

MySQL is a popular open-source relational database management system (RDBMS). Here’s what it does:

* `Organizes and manages data:` MySQL organizes data into tables, rows, and columns, which can be related to each other. This structure allows for efficient data management and retrieval.
    
* `Relational database:` Unlike other types of databases, MySQL is a relational database. This means it stores data in separate tables rather than putting all the data in one big storeroom. This makes it easier to maintain and access specific data.
    
* `SQL:` The “SQL” in MySQL stands for “Structured Query Language”, which is a standardized language used to access databases. Depending on your programming environment, you might enter SQL directly or use a language-specific API that hides the SQL syntax.
    
* `Open source:` Being open source means anyone can use and modify MySQL software for free. This has led to its widespread popularity and use in many applications, from small-scale projects to large-scale websites and enterprise-level solutions.
    
* `A popular choice for developers:` MySQL consistently ranks as the most popular database for developers. It supports various programming languages and platforms, and offers high performance, reliability, scalability, security, and flexibility.
    

In short, MySQL is a powerful tool for managing and manipulating structured data, making it a key component in many web applications and services. It’s different from other databases because of its open-source nature, its use of SQL, and its strong performance and reliability characteristics.

---

### Overview database common understanding:

1. Why not use storage volume, instead of database?
    
    While storage devices like hard drives, SSDs, and memory cards can store data, databases offer several advantages that make them more suitable for storing application data.
    
    `Storage Volumes` are like a big box where you can put anything, but if you need to find something specific quickly, it can be difficult and time-consuming. They are great for storing things like photos, videos, or documents, but not so good when you need to find, update, or analyze specific pieces of data quickly.
    
    `On the other hand, Databases` are like a well-organized filing cabinet with labels and categories, making it easy to find, update, or analyze specific data. They are designed to handle complex operations on data, like finding all customers who bought a specific product last month.
    
    Here are some reasons why we use databases instead of storage volumes for applications:
    
    * **Speed**: Databases are designed to handle complex queries, which allows applications to retrieve and update data much faster than they could if the data were stored in a storage volume.
        
    * **Concurrent Access**: Databases allow multiple users or applications to access and modify data at the same time without conflicts. This is crucial for applications where many users need to access and update data simultaneously.
        
    * **Data Integrity**: Databases have built-in mechanisms to ensure data integrity. They can enforce rules to prevent duplicate, missing, or incorrect data. This helps maintain the accuracy and consistency of data.
        
    * **Security**: Databases provide robust security features, including access control and encryption, to protect sensitive data from unauthorized access or modification.
        
    * **Scalability**: Databases can handle large amounts of data and can be scaled up or down to meet the needs of the application.
        
2. **What is a database?** A database is an organized collection of structured information, or data, typically stored electronically in a computer system.
    
    Databases help us store information in such a way that we can easily manipulate it. Each row in a table is called a record, and each cell is a field.
    
3. **Uses of a database in an application:** Databases are used in applications for storing, retrieving, and managing data. They are essential for data management, integration, privacy, collaboration, analysis, and reporting.
    
4. **Types of Databases:** There are several types of databases, including:
    
    * Relational databases
        
    * Non-relational (NoSQL) databases
        
    * Object-oriented databases
        
    * Centralized databases
        
    * Distributed databases
        
    * Cloud databases.
        
5. **Why different types of databases are made and their purpose:** Different types of databases are designed to meet specific requirements and to handle different types of data. For example, relational databases are best for structured data and complex queries, while non-relational databases are more flexible and can handle unstructured data.
    
6. **What is a relational database?** A relational database organizes data into tables (rows and columns), which can be joined together via a primary key or a foreign key. These unique identifiers demonstrate the different relationships that exist between tables.
    
7. **What is a non-relational database?** A non-relational database, also known as a NoSQL database, stores data in a non-tabular form, and tends to be more flexible than the traditional, SQL-based, relational database structures. It does not follow the relational model provided by traditional relational database management systems.
    
8. **What is a database language?** Database languages are a type of programming language used to define and manipulate a database. They are classified into four types: Data Definition Language (DDL), Data Manipulation Language (DML), Data Control Language (DCL), and Transaction Control Language (TCL).
    
9. **Why are Databases Important?** Databases are crucial for many reasons. They allow us to store, retrieve, and manipulate data in an efficient manner. They help in organizing data, ensuring data integrity, and providing a high level of data security.
    
10. **What are the Uses of Databases?** Databases are used in various ways. They are used for storing data, searching for specific information within the data, allowing multiple people to look at and change the data at the same time, managing who is allowed to see the data and who can change it, and managing rules about the data.
    
11. **What is a Cloud Database?** A cloud database is a database service built and accessed through a cloud computing platform. It serves many of the same functions as a traditional database with the added flexibility of cloud computing.
    
12. **Why Use a Cloud Database?** Cloud databases provide flexibility, reliability, security, affordability, and more. They can rapidly adapt to changing workloads and demands without increasing the workload of already overburdened teams.
    

Now we have learnt enough understandingn

---

1. # Install & Configure MySQL in Linux
    

> Note: Make sure you have
> 
> * Proper Internet connection and connectivity for package installation.
>     
> * Yum client configure at `/etc/yum.repos.d`
>     

* Install MySQL package in Linux Rhel-9
    

```plaintext
# yum install -y mysql-server
```

* Restart and enable the `mysqld.service`
    

```plaintext
# systemctl enable --now mysqld.service
# systemctl status mysqld
```

* Run `mysql_secure_installation` script, that is typically run after installing MySQL to ensure a more secure default setup.
    

```plaintext
# mysql_secure_installation
```

> The simplified explanation of `mysql_secure_installation`:
> 
> 1. `Sets root password:` If there’s no existing password for the MySQL root user, it prompts you to set one.
>     
> 2. `Removes anonymous users:` MySQL includes an anonymous user account by default. This script removes such accounts.
>     
> 3. `Disables remote root login:` It prevents root accounts from being accessed from outside the local host.
>     
> 4. `Removes test database:` MySQL includes a test database by default. This script removes this database.
>     
> 5. `Reloads privilege tables:` Finally, it reloads the privilege tables to make sure all changes take effect immediately.
>     

* Login to MySQL with default user `root` and newly set password through `mysql_secure_installation` script.
    

```plaintext
# mysql -u root -p
Enter password:
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 8.0.32 Source distribution

Copyright (c) 2000, 2023, Oracle and/or its affiliates.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql>
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">How to access MySQL database without entering username and password for security reasons.</div>
</div>

* Create a new file `~/.my.cnf` on your home directory and write some lines
    

```plaintext
# vim ~/.my.cnf

[client]
user=rakamodify
password=password

:wq!
```

Now you can log in MySQL without entering username and password.

```plaintext
# mysql

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 11
Server version: 8.0.32 Source distribution
Copyright (c) 2000, 2023, Oracle and/or its affiliates.
Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.
Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.
mysql>
```

---

1. # Submit SQL query for MySQL database interaction
    

* Create a new Database.
    

```sql
mysql> CREATE DATABASE wordpress;
mysql> SHOW DATABASES;
```

* Show newly created database Tables (If exists).
    

```sql
mysql> USE wordpress;
mysql> CREATE TABLE table1 (
    id INT AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100),
    PRIMARY KEY(id)
);

mysql> CREATE TABLE table2 (
    id INT AUTO_INCREMENT,
    post_title VARCHAR(200),
    post_content TEXT,
    PRIMARY KEY(id)
);
```

* Enter some records in data row/fields
    

```sql
mysql> INSERT INTO table1 (name, email) VALUES ('John Doe', 'john@example.com'), ('Jane Doe', 'jane@example.com');
mysql> INSERT INTO table2 (post_title, post_content) VALUES ('First Post', 'This is the content of the first post'), ('Second Post', 'This is the content of the second post');
```

* Describe Tables to see tables columns/attributes.
    

```sql
mysql> SHOW tables;
+---------------------+
| Tables_in_wordpress |
+---------------------+
| table1              |
| table2              |
+---------------------+
2 rows in set (0.00 sec)


mysql> DESCRIBE table1;
+-------+--------------+------+-----+---------+----------------+
| Field | Type         | Null | Key | Default | Extra          |
+-------+--------------+------+-----+---------+----------------+
| id    | int          | NO   | PRI | NULL    | auto_increment |
| name  | varchar(100) | YES  |     | NULL    |                |
| email | varchar(100) | YES  |     | NULL    |                |
+-------+--------------+------+-----+---------+----------------+
3 rows in set (0.00 sec)
```

* Show tables record.
    

```sql
mysql> 
mysql> SELECT * FROM table1;
+----+----------+------------------+
| id | name     | email            |
+----+----------+------------------+
|  1 | John Doe | john@example.com |
|  2 | Jane Doe | jane@example.com |
+----+----------+------------------+
2 rows in set (0.00 sec)

mysql> SELECT * FROM table2;
+----+-------------+----------------------------------------+
| id | post_title  | post_content                           |
+----+-------------+----------------------------------------+
|  1 | First Post  | This is the content of the first post  |
|  2 | Second Post | This is the content of the second post |
+----+-------------+----------------------------------------+
2 rows in set (0.00 sec)
```

* Create a new user for security.
    

```sql
mysql> CREATE USER 'username'@'host' IDENTIFIED WITH authentication_plugin BY 'password';
mysql> CREATE USER 'sammy'@'localhost' IDENTIFIED BY 'password';
mysql> CREATE USER 'sammy'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```

* Alter/Edit Modification of user creation.
    

```sql
mysql> ALTER USER 'sammy'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';
```

> **\*Imp: about creating a new**`MySQL user`**.**
> 
> Creating a new user for a MySQL database is important for several reasons:
> 
> 1. `Security:` Each user in MySQL has a set of permissions that determine what actions they can perform. By creating a new user, you can limit their permissions, reducing the risk of unauthorized access or changes to your database.
>     
> 2. `Access Control:` You can grant different users different levels of access to your databases. For example, you might have a user that can only read data from a database, but not modify it.
>     
> 3. `Accountability:` By having separate users, you can track who is making changes to your database. This can be useful for auditing purposes.
>     
> 4. `Resource Management:` MySQL allows you to set resource limits on a per-user basis. This can help prevent a single user from consuming too many resources.
>     
> 
> Remember, it’s always a good practice to follow the principle of least privilege, i.e., users should be given the minimum levels of access necessary to perform their tasks. This helps to maintain the integrity and security of your database.

* Grant privileges on a database for newly created user.
    

```sql
mysql> GRANT PRIVILEGE ON database.table(s) TO 'username'@'host';
mysql> GRANT CREATE, ALTER, DROP, INSERT, UPDATE, DELETE, SELECT, REFERENCES, RELOAD on *.* TO 'sammy'@'localhost' WITH GRANT OPTION;   
mysql> GRANT ALL PRIVILEGES ON *.* TO 'username'@'localhost' WITH GRANT OPTION;
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">During MySQL login, make sure your hostname should be exactly as you mentioned during user grant creation. For Example:- <code>'username'@'localhost'</code></div>
</div>

* Refresh the MySQL changes immediately.
    

```sql
mysql> FLUSH PRIVILEGES;
```

---

1. # Database Backup & Restore safely
    

* To backup a MySQL database
    
    <div data-node-type="callout">
    <div data-node-type="callout-emoji">💡</div>
    <div data-node-type="callout-text">First, exit the MySQL command shell. Then, execute the following command in the Linux terminal.</div>
    </div>
    

```plaintext
# mysqldump -u username -p database-name > /var/lib/mysql/mysql_backup.sql
Enter Password:
```

Please replace `[username]`, `[password]`, `[database_name]`, and `[filename]` with your MySQL username, password, the name of the database you want to backup, and the name you want for the backup file, respectively.

Remember, there is no space between `-p` and your password. If your password contains special characters, you might need to put it in quotes. Also, make sure you have the necessary permissions to perform the backup.

* **Restore backup of MySQL database**
    

```plaintext
# mysql -u username -p database-name < /var/lib/mysql/mysql_backup.sql
Enter Password:
```

---

# Important questions

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Basic Intermediate Level Questions:-</div>
</div>

1. **Q: What is SQL?**
    
    A: SQL stands for Structured Query Language. It’s a standard language for managing and manipulating databases.
    
2. **Q: What is a primary key?**
    
    A: A primary key is a unique identifier for a record in a database table. No two records in a table can have the same primary key value.
    
3. **Q: What is a foreign key?**
    
    A: A foreign key is a column or set of columns in a table that is used to establish a link between the data in two tables.
    
4. **Q: What is a database schema?**
    
    A: A database schema is the structure of a database system, described in a formal language supported by the database management system.
    
5. **Q: What is a database transaction?**
    
    A: A database transaction is a unit of work that is performed against a database. It’s the propagation of one or more changes to the database.
    
6. **Q: What is database normalization?**
    
    A: Database normalization is the process of organizing data in a database in the most efficient way possible. It involves dividing a database into two or more tables and defining relationships between the tables.
    
7. **Q: What is a data model?**
    
    A: A data model is a conceptual representation of data structures required for a database and is used as a blueprint for designing databases.
    
8. **Q: What is a query?** A:
    
    A query is a request for data or information from a database table or combination of tables.
    
9. **Q: What is a database view?**
    
    A: A database view is a searchable object in a database that is defined by a query.
    
10. **Q: What is a database index?**
    
    A: A database index is a data structure that improves the speed of data retrieval operations on a database table.
    
11. **Q: What is a stored procedure?**
    
    A: A stored procedure is a prepared SQL code that you can save, so the code can be reused over and over again.
    
12. **Q: What is a trigger in a database?**
    
    A: A trigger is a stored procedure in a database that automatically reacts to an event like insertions, updates, or deletions.
    
13. **Q: What is a cursor in a database?**
    
    A: A cursor in a database is a control structure that enables traversal over the records in a database.
    
14. **Q: What is a database constraint?**
    
    A: A database constraint is a rule that is applied to a field or set of fields in a table, which limits the data that can be stored in fields.
    
15. **Q: What is a database join?**
    
    A: A database join is a method of combining rows from two or more tables based on a related column between them.
    
16. **Q: What is a database lock?** A: A database lock is a mechanism used by DBMS to control read/write access to a database or to a portion of it.
    
17. **Q: What is a database transaction log?**
    
    A: A database transaction log is a history of all actions executed by a database management system to ensure data integrity and to facilitate data recovery.
    
18. **Q: What is a database shard?**
    
    A: A database shard is a horizontal partition of data in a database, where each shard is held on a separate database server instance.
    
19. **Q: What is a database replica?**
    
    A: A database replica is a copy of a database on a different server or on the same server as the primary database.
    
20. **Q: What is a database rollback?** A: A database rollback is an operation which returns the database to some previous state.
    
21. **Q: What is a database commit?**
    
    A: A database commit is an operation that gives a green signal to the database management system to finalize the changes, and after this operation, no change can be reverted back.
    
22. **Q: What is a database deadlock?**
    
    A: A database deadlock is a situation where two transactions wait for each other to give up locks.
    
23. **Q: What is a database backup?**
    
    A: A database backup is a copy of the data from a database that can be used to reconstruct data.
    
24. **Q: What is a database recovery?**
    
    A: Database recovery is the process of restoring the database back to the correct state at a given point of time in case of a failure.
    
25. **Q: What is a database schema?**
    
    A: A database schema is the skeleton structure that represents the logical view of the entire database.
    
26. **Q: What is a database cluster?**
    
    A: A database cluster is a group of databases that work together to maintain high availability and data redundancy.
    
27. **Q: What is AWS?**
    
    A: AWS stands for Amazon Web Services. It’s a platform by Amazon that provides on-demand cloud computing platforms and APIs to individuals, companies, and governments.
    
28. **Q: What is cloud computing?**
    
    A: Cloud computing is the delivery of computing services over the internet (“the cloud”) including servers, storage, databases, networking, software, analytics, and intelligence.
    
29. **Q: What is a cloud database?**
    
    A: A cloud database is a database service built and accessed through a cloud platform. It serves many of the same functions as a traditional database with the added flexibility of cloud computing.
    
30. **Q: What is the importance of cloud databases?**
    
    A: Cloud databases provide scalability, high availability, multi-regional distribution, and disaster recovery capabilities. They can be accessed from anywhere in the world, at any time, making data management more convenient.
    
31. **Q: What is AWS RDS?**
    
    A: Amazon RDS (Relational Database Service) is a web service that makes it easier to set up, operate, and scale a relational database in the cloud.
    
32. **Q: What is a database backup?**
    
    A: A database backup is a copy of the data from a database that can be used to reconstruct data.
    
33. **Q: What is the importance of database backup?**
    
    A: Database backups are crucial for protecting data against loss due to hardware failures, user errors, and natural disasters. They allow you to restore your data and continue business operations.
    
34. **Q: What is database restore?**
    
    A: Database restore is the process of bringing back a database from a backup to its original place or to a new place.
    
35. **Q: How does AWS handle database backup and restore?**
    
    A: AWS provides services like Amazon RDS which automatically backs up your data and allows you to perform a point-in-time restore.
    
36. **Q: What is AWS S3?**
    
    A: Amazon S3 (Simple Storage Service) is an object storage service that offers industry-leading scalability, data availability, security, and performance.
    
37. **Q: How is AWS S3 used in database backup?**
    
    A: Amazon S3 is often used to store database backups in a secure and scalable environment. Database backup files can be moved to S3 and restored when needed.
    
38. **Q: What is AWS DynamoDB?**
    
    A: Amazon DynamoDB is a key-value and document database that delivers single-digit millisecond performance at any scale.
    
39. **Q: What is the difference between SQL and NoSQL databases?**
    
    A: SQL databases are primarily called as Relational Databases (RDBMS), whereas NoSQL database are primarily called as non-relational or distributed databases.
    
40. **Q: What is AWS EC2?**
    
    A: Amazon EC2 (Elastic Compute Cloud) is a web service that provides resizable compute capacity in the cloud. It is designed to make web-scale cloud computing easier for developers.
    
41. **Q: What is the role of AWS EC2 in database hosting?**
    
    A: Amazon EC2 instances can be used to host databases. The service provides flexible, resizable capacity in the AWS Cloud which can be used to install and run any third-party database software.
    
42. **Q: What is AWS Lambda?**
    
    A: AWS Lambda is a serverless compute service that lets you run your code without provisioning or managing servers.
    
43. **Q: How does AWS Lambda interact with databases?**
    
    A: AWS Lambda can interact with databases by executing SQL statements, reading and writing data, and performing other database operations in response to events.
    
44. **Q: What is the importance of AWS in database management?**
    
    A: AWS provides a broad and deep set of database services that provide innovative and scalable solutions for database management. These services are fully managed, relieving the burden of server maintenance and setup.
    
45. **Q: What is database migration?**
    
    A: Database migration is the process of moving your data from one database to another.
    
46. **Q: What is AWS DMS?**
    
    A: AWS DMS (Database Migration Service) helps you migrate databases to AWS quickly and securely. The source database remains fully operational during the migration, minimizing downtime to applications that rely on the database.
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>Now lets move to Intermediate &amp; Advance Level questions:-</strong></div>
</div>

1. **<mark>Question-1:</mark> What does the**`GRANT` statement do in MySQL?
    
    Answer-1: The `GRANT` statement in MySQL is used to give privileges to a user account. It allows the database administrator to define the kinds of operations that a user can perform.
    
2. **<mark>Question-2: </mark> Can you explain what each of the permissions in the**`GRANT` statement (`CREATE`, `ALTER`, `DROP`, `INSERT`, `UPDATE`, `DELETE`, `SELECT`, `REFERENCES`, `RELOAD`) allows a user to do?
    
    Answer-2: The permissions in the `GRANT` statement allow a user to perform various operations:
    
    * `CREATE`: Allows the user to create databases and tables.
        
    * `ALTER`: Allows the user to modify existing databases and tables.
        
    * `DROP`: Allows the user to delete databases, tables, and views.
        
    * `INSERT`: Allows the user to insert data into tables.
        
    * `UPDATE`: Allows the user to update existing data in tables.
        
    * `DELETE`: Allows the user to delete data from tables.
        
    * `SELECT`: Allows the user to read data using the SELECT statement.
        
    * `REFERENCES`: Allows the user to create a foreign key constraint.
        
    * `RELOAD`: Allows the user to reload the server settings and flush the server logs.
        
3. **<mark>Question-3</mark>: In the query, what does**`*.*` represent?
    
    Answer-3: In a MySQL query, `*.*` represents all databases and all tables within those databases. It’s a wildcard notation where the first `*` stands for all databases and the second `*` stands for all tables.
    
4. **<mark>Question-4</mark>: What does the**`WITH GRANT OPTION` clause do in a `GRANT` statement?
    
    Answer-4: The `WITH GRANT OPTION` clause in a `GRANT` statement allows the user to grant any privileges they have to other users. It’s a way to delegate authority within the database system.
    
5. **<mark>Question-5</mark>: Why might you want to create a new user in MySQL, like ‘sammy’ in the given query?**
    
    Answer-5: Creating a new user in MySQL, like ‘sammy’, allows you to control access to your databases. Each user can be given specific privileges, ensuring they can only perform the actions necessary for their role. This helps maintain the security and integrity of your databases.
    
6. **<mark>Question-6</mark>: What are some potential security implications of granting a user too many permissions in MySQL?**
    
    Answer-6: Granting a user too many permissions in MySQL can lead to several security issues. The user could accidentally or maliciously modify or delete important data. They could also potentially access sensitive information. It’s best to follow the principle of least privilege, granting only the permissions necessary for the user’s role.
    
7. **<mark>Question-7</mark>: How would you modify the permissions of an existing user in MySQL?**
    
    Answer-7: To modify the permissions of an existing user in MySQL, you can use the `GRANT` statement to add new permissions and the `REVOKE` statement to remove permissions. After modifying permissions, you should use the `FLUSH PRIVILEGES` command to ensure the changes take effect immediately.
    
8. **<mark>Question-8</mark>: How can you revoke permissions from a user in MySQL?**
    
    Answer-8: You can revoke permissions from a user in MySQL using the `REVOKE` statement, followed by the privileges you want to remove, and then the `FROM` keyword followed by the username. For example, `REVOKE SELECT, INSERT ON database.table FROM 'username'@'`[`localhost`](http://localhost)`';`.
    
9. **<mark>Question-9</mark>: Can you explain the principle of least privilege and why it’s important in the context of database access control?**
    
    Answer-9: The principle of least privilege is a computer security concept in which a user is given the minimum levels of access necessary to complete their job functions. In the context of database access control, this principle helps to protect data from accidental or malicious modification, deletion, or exposure.
    
10. <mark>Question-10:</mark>**What happens if you change your hostname, then can you access your MySQL database?**
    
    Answer: Changing the hostname of your machine does not directly affect your ability to access your MySQL database. However, if your MySQL users or permissions are set up to only allow connections from a specific hostname, you may need to update these settings. Also, any applications that connect to MySQL using the old hostname will need to be updated.
    
11. <mark>Question-11 </mark> : **How to give single table’s authority permission on a database for a user?**
    
    Answer: You can grant specific table permissions to a user in MySQL using the `GRANT` command. Here’s an example:
    
    ```sql
    GRANT SELECT, INSERT, UPDATE ON database_name.table_name TO 'username'@'localhost';
    ```
    
    Note:- This command gives `SELECT`, `INSERT`, and `UPDATE` permissions on `table_name` in `database_name` to the user `username` connecting from [`localhost`](http://localhost).
    
12. **<mark>Question-13</mark>: What is the MySQL configuration file?**
    
    Answer: The MySQL configuration file is a setup file for MySQL server. It’s named `my.cnf` on Unix-based systems and `my.ini` on Windows. This file is used to configure various server settings like the number of concurrent connections, table cache size, memory settings, and more.
    
13. <mark>Question-14</mark>: **Can you access MySQL from another machine on LAN?**
    
    Answer: Yes, you can access MySQL from another machine on the same Local Area Network (LAN), provided that the MySQL server is configured to accept network connections and the necessary firewall rules allow it. The user must also have the necessary permissions to connect from the client machine’s IP address.
    
14. **<mark>Question-15:</mark> Can you access MySQL database on a different port like 3307?**
    
    Answer: Yes, you can access a MySQL database on a different port like 3307. By default, MySQL listens on port 3306, but this can be changed in the MySQL configuration file. When connecting, you would specify the port number along with the hostname, like `mysql -h hostname -P 3307 -u username -p`.
    

---

# References Links:

* `How to create a new user in MySQL and grants permission:`[https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)
    
* `Learn MySQL SQL query:-`[https://www.w3schools.com/MySQL/default.asp](https://www.w3schools.com/MySQL/default.asp)