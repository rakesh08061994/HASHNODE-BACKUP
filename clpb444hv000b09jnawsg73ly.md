---
title: "Effortless Database Dominance: Seamlessly Manage Multiple SQL Servers Alongside MariaDB Galera Cluster on RHEL 9 for Optimal Performance!"
datePublished: Thu Nov 23 2023 11:30:43 GMT+0000 (Coordinated Universal Time)
cuid: clpb444hv000b09jnawsg73ly
slug: effortless-database-dominance-seamlessly-manage-multiple-sql-servers-alongside-mariadb-galera-cluster-on-rhel-9-for-optimal-performance
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1700739740004/b0ece5fd-a9d0-4b5c-a63c-33e597c132ee.png
tags: linux, wordpress, development, mysql, backend, database, devops, mariadb, frontend-development, serverless, backup, cluster, devops-articles, devops-journey, galera-cluster

---

### What is "Galera Cluster" and why this is so important ?

> `Definition-1`: Enterprises choose Galera Cluster because it provides most robust solution against data loss, MySQL and MariaDB high availability and scalability. You must see the case study : [https://galeracluster.com/references/](https://galeracluster.com/references/)
> 
> `Definition-2:` The big plus is that all nodes have exact the same information, and no node is running for even a fraction of a second behind. This will also mean that no information will be lost!
> 
> `Definition-3:` MySQL master/slave setup was just too fragile and needed regular work to fix each time the slave got out of sync. Now with Galera we've found that even if we take a node offline for a while, it re-syncs automatically  
> and without intervention. Must see this Case-Study : [https://galeracluster.com/wp-content/uploads/2018/01/galera-casestudy-mercadolibre.pdf](https://galeracluster.com/wp-content/uploads/2018/01/galera-casestudy-mercadolibre.pdf)

We are going to create Mini Galera Cluster for practice. For this, we use Virtual Machine (with a high H/W configuration) or any cloud service . WordPress will be in the front end and Gallera cluster will be on the back end to manage multiple MySQL servers simontenously.

## **Step-1 (Environment Specification:)**

We are using three identical [Rhel Linux 9](https://www.centlinux.com/2022/07/rocky-linux-9-minimal-server-install.html) Ec2-Instances with following specifications.

* **ec2.small Instance AWS**
    
* **Memory** - 2 GB
    
* **Storage** - 40 GB
    
* **Operating System** - Rhel Linux release 9
    
* **Hostname** - mariadb-01, mariadb-02, mariadb-03
    
* **IP Address** - (192.168.18.88, 192.168.18.89, 192.168.18.90)/24
    

---

## **Step-2 (Configure Name Resolution):**

Setup Local DNS resolution, so your Cluster nodes do not depend upon a DNS server for name resolution.

Login to your First MariaDB node as **root** user.

Edit /etc/hosts file by using a **vim** text editor.

```sql
# vi /etc/hosts
```

Adding following lines in this file.

```sql
192.168.18.88 mariadb-01 mariadb-01.centlinux.com
192.168.18.89 mariadb-02 mariadb-02.centlinux.com
192.168.18.90 mariadb-03 mariadb-03.centlinux.com
```

Now, use **scp** command to copy your updated **hosts** file on remaining database nodes. But make sure you have enough rights to access other machines through ssh or scp. If not do that on each machine.

```sql
# vi /etc/ssh/sshd_config


PermitRootLogin yes
PubkeyAuthentication yes
PermitEmptyPasswords yes
PasswordAuthentication yes

:wq!
```

```sql
# systemctl restart sshd
```

And then you can share /etc/hosts configuration file by `scp`

```sql
# scp /etc/hosts root@mariadb-02:/etc/hosts
# scp /etc/hosts root@mariadb-03:/etc/hosts
```

---

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Only If you using Local Server for your galera cluster. Then follow Step 3 &amp; 3.1</div>
</div>

## **Step-3 (Configure Linux Firewall):**

If you are setting up galera cluster on local VM servers, Execute following commands on each MariaDB node to allow **galera** service in Linux firewall.

```plaintext
---Open TCP port 3306 (MySQL Default Trrafic)
# firewall-cmd --zone=public --add-port=3306/tcp --permanent
success

----Open TCP port 4567 (Galera Cluster Communication)
# firewall-cmd --zone=public --add-port=4567/tcp --permanent
success

----Open UDP port 4567
# firewall-cmd --zone=public --add-port=4567/udp --permanent
success

----Open TCP port 4444 (Incremental state transfer)
# firewall-cmd --zone=public --add-port=4444/tcp --permanent
success

----Open TCP port 4568 (state snapshot transfer)
# firewall-cmd --zone=public --add-port=4568/tcp --permanent
success

# firewall-cmd --permanent --add-service=galera
success

# systemctl restart firewalld

# firewall-cmd --reload
Reload success
```

## Step-3.1 (Open ports for galera in selinux)

```sql
# semanage port -a -t mysqld_port_t -p tcp 3306
# semanage port -a -t mysqld_port_t -p tcp 4444
# semanage port -a -t mysqld_port_t -p tcp 4567
# semanage port -a -t mysqld_port_t -p udp 4567
# semanage port -a -t mysqld_port_t -p udp 4568
# semanage permissive -a mysqld_t
```

---

## **Step-4 (Update Software Packages):**

Execute follow set of commands on each cluster node to update software packages and note down the Linux OS and Linux Kernel versions.

```sql
# dnf update -y

# uname -r
5.14.0-284.11.1.el9_2.x86_64
```

---

## **Step-5 (Installing Galera Server):**

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>Note: Install MariaDB Yum Repository:</strong></div>
</div>

you need to install MariaDB Official yum repository by using following Linux command.

```sql
# curl -LsS https://r.mariadb.com/downloads/mariadb_repo_setup | sudo bash


# [info] Checking for script prerequisites.
# [info] MariaDB Server version 10.11 is valid
# [info] Repository file successfully written to /etc/yum.repos.d/mariadb.repo
# [info] Adding trusted package signing keys...
#/etc/pki/rpm-gpg ~
#~
# [info] Successfully added trusted package signing keys
# [info] Cleaning package cache...
25 files removed
```

Build your yum cache for newly installed yum repositories.

```sql
# dnf makecache


MariaDB Server                                   33 kB/s | 690 kB     00:20
MariaDB MaxScale                                469  B/s | 7.1 kB     00:15
MariaDB Tools                                   3.8 kB/s |  25 kB     00:06
AWS Linux 9 - BaseOS                           65 kB/s | 1.9 MB     00:29
AWS Linux 9 - AppStream                       117 kB/s | 7.1 MB     01:01
AWS Linux 9 - Extras                          427  B/s |  10 kB     00:23
Metadata cache created.
```

Execute following **dnf** command on each node of cluster to install MariaDB Galera Server. (Don't start mariadb server for now. wait )

```sql
# dnf install -y mariadb-server-galera
```

Now, connect to your first node as **root** user and edit Galera configuration file in **vim** text editor.

```sql
# vi /etc/my.cnf.d/galera.cnf
```

Locate and set following directives in this file.

```sql
# Enable wsrep
wsrep_on=1

# Logical cluster name. Should be the same for all nodes.
wsrep_cluster_name="mariadb_cluster"

# Group communication system handle
wsrep_cluster_address="gcomm://192.168.18.88,192.168.18.89,192.168.18.90"

# Base replication <address|hostname>[:port] of the node.
# The values supplied will be used as defaults for state transfer receiving,
# listening ports and so on. Default: address of the first network interface.
wsrep_node_address="192.168.18.88"
```

Start Galera cluster on first node.

```sql
# galera_new_cluster
```

Enable and start MariaDB database service.

```sql
# systemctl enable --now mariadb.service
Created symlink /etc/systemd/system/mysql.service → /usr/lib/systemd/system/mariadb.service.
Created symlink /etc/systemd/system/mysqld.service → /usr/lib/systemd/system/mariadb.service.
Created symlink /etc/systemd/system/multi-user.target.wants/mariadb.service → /usr/lib/systemd/system/mariadb.service
```

Configure initial settings of your MariaDB server as follows.

```sql
# mysql_secure_installation

NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MariaDB
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!

In order to log into MariaDB to secure it, we'll need the current
password for the root user. If you've just installed MariaDB, and
haven't set the root password yet, you should just press enter here.

Enter current password for root (enter for none):
OK, successfully used password, moving on...

Setting the root password or using the unix_socket ensures that nobody
can log into the MariaDB root user without the proper authorisation.

You already have your root account protected, so you can safely answer 'n'.

Switch to unix_socket authentication [Y/n] n
 ... skipping.

You already have your root account protected, so you can safely answer 'n'.

Change the root password? [Y/n] Y
New password:
Re-enter new password:
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MariaDB installation has an anonymous user, allowing anyone
to log into MariaDB without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] Y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] Y
 ... Success!

By default, MariaDB comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] Y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] Y
 ... Success!

Cleaning up...

All done!  If you've completed all of the above steps, your MariaDB
installation should now be secure.

Thanks for using MariaDB!
```

Login to your MariaDB Database server by using **mysql** command.

```sql
# mysql -u root -p
Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 16
Server version: 10.5.16-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement
```

Check the value to **wsrep\_cluster\_size** variable to get the number of nodes in your Galera cluster.

```sql
MariaDB [(none)]> show global status like 'wsrep_cluster_size';
+--------------------+-------+
| Variable_name      | Value |
+--------------------+-------+
| wsrep_cluster_size | 1     |
+--------------------+-------+
1 row in set (0.001 sec)
```

Currently, there is only one node in your Galera cluster.

---

## **Step-6 (Adding Nodes in Galera Cluster):**

Your Galera Cluster has been started successfully, now you can add other nodes in your Galera cluster.

Login to your second node as **root** user and edit Galera configuration file.

```sql
# ssh root@mariadb-02
# vi /etc/my.cnf.d/galera.cnf
```

Set following directives in this file.

```sql
# Enable wsrep
wsrep_on=1

# Logical cluster name. Should be the same for all nodes.
wsrep_cluster_name="mariadb_cluster"

# Group communication system handle
wsrep_cluster_address="gcomm://192.168.18.88,192.168.18.89,192.168.18.90"

# Base replication <address|hostname>[:port] of the node.
# The values supplied will be used as defaults for state transfer receiving,
# listening ports and so on. Default: address of the first network interface.
wsrep_node_address="192.168.18.89"
```

Enable and start MariaDB database service.

```sql
# systemctl enable --now mariadb
```

Login to your MariaDB Database server by using **mysql** command.

```sql
# mysql -u root -p
Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 16
Server version: 10.5.16-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement
```

Check the status of **wsrep\_cluster\_size** variable again.

```sql
MariaDB [(none)]> show global status like 'wsrep_cluster_size';
+--------------------+-------+
| Variable_name      | Value |
+--------------------+-------+
| wsrep_cluster_size | 2     |
+--------------------+-------+
1 row in set (0.002 sec)
```

You can see that, after addition of second node, your Galera Cluster size is become 2.

Similarly, you can add your third node to Galera cluster.

```sql
# ssh root@mariadb-03
# vi /etc/my.cnf.d/galera.cnf
```

Set following directives in Galera configuration file.

```sql
# Enable wsrep
wsrep_on=1

# Logical cluster name. Should be the same for all nodes.
wsrep_cluster_name="mariadb_cluster"

# Group communication system handle
wsrep_cluster_address="gcomm://192.168.18.88,192.168.18.89,192.168.18.90"

# Base replication <address|hostname>[:port] of the node.
# The values supplied will be used as defaults for state transfer receiving,
# listening ports and so on. Default: address of the first network interface.
wsrep_node_address="192.168.18.90"
```

Enable and start MariaDB database service.

```sql
# systemctl enable --now mariadb
```

Login to your MariaDB Database server by using **mysql** command.

```sql
# mysql -u root -p
Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 16
Server version: 10.5.16-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement
```

Check the value of **wsrep\_cluster\_size** variable again.

```sql
MariaDB [(none)]> show global status like 'wsrep_cluster_size';
+--------------------+-------+
| Variable_name      | Value |
+--------------------+-------+
| wsrep_cluster_size | 3     |
+--------------------+-------+
1 row in set (0.002 sec)
```

All three nodes have been successfully added to your MariaDB cluster.

You can test your Galera cluster by creating some database objects on one node and check if the changes reflect to other nodes in real time.

---

### Step-7 (Create a database and insert some tables, and records to check Galera cluster)

> Access the login using the first instance only. This MySQL Galera server connects to your frontend application and distributes the same database records to its slave cluster database nodes

```sql
# mysql -u root -p
Enter password:
```

> We can access database without assigning username and password. For this you have to go home directory of root and write some configuration under `~/.my.cnf`

```sql
[root@galera1 ~]# vi ~/.my.cnf

[clients]
username="root"
password="password"

:wq!
```

Now login MySQL without assigning username and password:

```sql
# mysql

Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 16
Server version: 10.5.16-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement
```

```sql
MariaDB [(none)]> CREATE DATABASE wordpress;

MariaDB [(none)]> USE wordpress;
[Database Changed]

MariaDB [(wordpress)]> CREATE TABLE authors (id INT, name VARCHAR(20), email VARCHAR(20));
MariaDB [(wordpress)]> INSERT INTO authors (id,name,email) VALUES(1,"Vivek","xuz@abc.com");
MariaDB [(wordpress)]> INSERT INTO authors (id,name,email) VALUES(2,"Priya","p@gmail.com");
MariaDB [(wordpress)]> INSERT INTO authors (id,name,email) VALUES(3,"Tom","tom@yahoo.com");
MariaDB [(wordpress)]> INSERT INTO authors (id,name,email) VALUES(4,"Jerry","jerry@yahoo.com");

MariaDB [(wordpress)]> SHOW TABLES;
MariaDB [(wordpress)]> DESCRIBE authors;
MariaDB [(wordpress)]> SELECT * FROM authors;
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Now check same database entry on other slave Galera cluster nodes.</div>
</div>

Congratulations you've done it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1700810837961/47e4b0a7-94c3-4057-a6d8-d94f8bcc0482.jpeg align="center")

For any query, write it in the comment section.

---

### References:

* [https://www.symmcom.com/docs/how-tos/databases/how-to-configure-mariadb-galera-cluster-on-centos-7](https://www.symmcom.com/docs/how-tos/databases/how-to-configure-mariadb-galera-cluster-on-centos-7)
    
* [https://galeracluster.com/](https://galeracluster.com/)
    
* [https://galeracluster.com/library/training/videos/galera-mysql-installing.html](https://galeracluster.com/library/training/videos/galera-mysql-installing.html)