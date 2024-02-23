---
title: "Deploy WordPress + MariaDB + PHP + Apache web server on rhel9 with easy steps"
datePublished: Thu Jan 18 2024 13:02:34 GMT+0000 (Coordinated Universal Time)
cuid: clrj81y3a000109ky0z6pbp9s
slug: deploy-wordpress-mariadb-php-apache-web-server-on-rhel9-with-easy-steps
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705582695822/5d770ccd-ba82-4f40-bf87-04e55614634d.png
tags: project, linux, wordpress, mysql, php, projects, devops, mariadb, linux-for-beginners, linux-basics, linux-server, rocky-linux, rhel9, step-by-step, rakamodify

---

---

# Pre-Setup:

I am assuming that you have

* Configured the yum client and EPEL repository on the machine.
    
* Hostname
    
* Proper Network Internet connection for package installation
    

---

1. # Install Apache Web Server
    

* httpd packages for the web-server
    

```plaintext
# yum install -y httpd
```

* Restart the `httpd.service` and enable it
    

```plaintext
# systemctl enable --now httpd
```

* Add http & https package in the firewall & reload the firewall service
    

```plaintext
# firewall-cmd --permanent --add-port=80/tcp
# firewall-cmd --permannet --add-port=443/tcp
# firewall-cmd --reload
# firewall-cmd --list-all
```

* check the selinux label `object_r:httpd_sys_content_t` on `/var/www/html/`
    

```plaintext
# ls -lZ /var/www/html
-rw-r--r--.  1 root root unconfined_u:object_r:httpd_sys_content_t:s0      405 Feb  6  2020 index.html 
```

* Check the HTTP web server page on the browser
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705579805659/1da575e2-71be-4576-be41-79c37bc61ee6.png align="center")

Congratulations!

your apache web server is working perfectly. Let's Move further for MySQL + WordPress configuration.

---

1. # Install MariaDB/MySQL and WordPress
    

* For this first, we have to set setup the [`"REMI"`](https://repo.extreme-ix.org/remi/) repository client on the yum repository for `PHP` packages.
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Check your OS version <code>/etc/os-release</code> before configuring the REMI repository.</div>
</div>

```plaintext
# cat /etc/os-release

[root@mh1 conf]# cat /etc/os-release


NAME="Red Hat Enterprise Linux"
VERSION="9.1 (Plow)"
REDHAT_SUPPORT_PRODUCT_VERSION="9.1"
```

* Setup REMI repository for RHEL 9.1
    

```plaintext
# dnf install https://repo.extreme-ix.org/remi/enterprise/remi-release-9.rpm
# yum repolist all
```

* Install PHP packages `(php, php-mysqlnd, php-pdo, php-gd, php-mbstring)`
    

```plaintext
# yum install php php-mysqlnd php-pdo php-gd php-mbstring
```

* Install MySQL/MariaDB & Restart the service
    

```plaintext
# yum install -y mariadb-server mariadb
# yum enable --now mariadb.service
```

* Fresh configure your MariaDB
    

```plaintext
#  mariadb-secure-installation
```

* Get into MariaDB using new login
    

```plaintext
# mysql -u root -p
password:

Welcome to the MariaDB monitor.  Commands end with ; or \g.
Your MariaDB connection id is 13
Server version: 10.5.22-MariaDB MariaDB Server

Copyright (c) 2000, 2018, Oracle, MariaDB Corporation Ab and others.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

MariaDB [(none)]>
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Create a <code>~/.my.cnf</code> file and write some lines</div>
</div>

```plaintext
# vim ~/.my.cnf
[clients]
username=root
password=password

:wq!
```

Now you don't need to use `-u` & `-p` option to work with the MariaDB database.

```plaintext
# mysql
```

* Create a new database, user and grant permission on the database.
    

```plaintext
# mysql

MariaDB [(none)]> CREATE DATABASE wordpress;
MariaDB [(none)]> CREATE USER 'admin'@'localhost' IDENTIFIED BY 'password';     
MariaDB [(none)]> GRANT ALL PRIVILEGES ON wordpress.* TO 'admin'@'localhost' WITH GRANT OPTION;
MariaDB [(none)]> FLUSH PRIVILIGES;
```

---

1. # Install WordPress and configuration
    

* Go to `wordpress.org` and download the latest WordPress suit package using `wget.`
    

```plaintext
# cd /var/www/html/
# wget https://wordpress.org/latest.zip
# unzip latest.zip
# rm -rf latest.zip
```

* Configure `/var/www/html/wordpress/wp-config-sample.php` or `wp-config.php` configuration file
    

```plaintext
# vim /var/www/html/wordpress/wp-config-sample.php


// ** Database settings - You can get this info from your web host ** //
/** The name of the database for WordPress */
define( 'DB_NAME', 'wordpress' );

/** Database username */
define( 'DB_USER', 'admin' );

/** Database password */
define( 'DB_PASSWORD', 'password' );

/** Database hostname */
define( 'DB_HOST', 'localhost' );
```

* Open `/etc/httpd/conf/httpd.conf` file for above configuration.
    

```plaintext
# vim /etc/httpd/conf/httpd.conf

Listen 80
User apache
Group apache
ServerAdmin admin@localhost
DocumentRoot "/var/www/html/wordpress"
```

* Change `user:group` ownership to `apache` user on DocumentRoot directory
    

```plaintext
# chown -R apache:apache /var/www/html/wordpress
# ls -lZ /var/www/html/wordpress
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">NOTE: SELinux label <code>httpd_sys_content_t</code> &amp; user, group ownership should look like this:- <code>apache apache</code></div>
</div>

```plaintext
[root@mh1 conf]# ls -lZ /var/www/html/wordpress/
total 228
-rw-r--r--.  1 apache apache unconfined_u:object_r:httpd_sys_content_t:s0      405 Feb  6  2020 filename.extention  
```

* Restart the httpd.service, mariadb.service one more time to update with new changes.
    

```plaintext
# systemctl restart httpd.service  mariadb.service
# systemctl enable httpd.service mariadb.service
```

* Open your browser and paste this address: `http://machine-ip` .
    
* Fill your information and login WordPress Page.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705582627251/917bad02-a6d4-4a8f-b4fe-df88fe9ad6ff.png align="center")
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705582064228/16f7813a-ac66-4638-9a47-7acdc43e01d2.png align="right")

### *Lots of Congratulations!*

---