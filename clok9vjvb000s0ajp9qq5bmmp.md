---
title: "How to distribute traffic load between docker container web servers using nginx load balancer."
datePublished: Sat Nov 04 2023 16:42:14 GMT+0000 (Coordinated Universal Time)
cuid: clok9vjvb000s0ajp9qq5bmmp
slug: how-to-distribute-load-between-linux-servers-using-haproxy-load-balancer
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/3GZNPBLImWc/upload/a8d658123c708b4ecced10cd79d23e2d.jpeg
tags: linux, aws, nginx, configuration, load-balancing

---

I am using two AWS Instance server with different configuration. Details are:-First of all we will setup docker installation on server1 and run application with 2 docker containers.

| Server Hostname | Private Ipv4 | Public IPv4 | Configuration |
| --- | --- | --- | --- |
| dockerserver.example.com | 172.31.84.250 | 54.175.218.1 | T2.medium + 20 GB storage + 2 core cpu + 4 GB RAM |
| loadserver.example.com | 172.31.32.25 | 54.175.228.52 | T2.Micro (Default) |

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699103410342/74fd5b13-c8e2-4b2d-b039-ba3e47796729.png align="center")

> Note: I am using Mobaxterm for AWS instances remote access on Windows OS
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699071604862/904a6f5c-2ede-4ec2-bfb9-870262f50038.png align="center")

---

## On Docker-Server ([54.175.218.1](http://54.175.218.1:8082/))

### Step-1 (How to setup docker on server machine with Ubuntu OS )

> we do follow official documentation for this: [https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)

```bash
$ sudo for pkg in docker.io docker-doc docker-compose docker-compose-v2 podman-docker containerd runc; do sudo apt-get remove $pkg; done
# Add Docker's official GPG key:
$ sudo apt-get update
$ sudo apt-get install ca-certificates curl gnupg
$ sudo install -m 0755 -d /etc/apt/keyrings
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
$ sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources:
$ echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
$ sudo apt-get update
$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

### Step-2 (Manage Docker as a non-root user.)

```bash
# add a new user ram and give password to him
ubuntu@docker~$ sudo adduser ram

$ sudo vim /etc/sudoers.d/ram
ram    ALL=(ALL) NOPASSWD: /usr/bin/docker    #Give docker related authorized permission

$ sudo systemctl restart  sshd 

#  run docker container with Non-Root user 
$ sudo usermod -aG docker ram    # Make ram as a secondary group member of docker group
$ su - ram
$ docker version
$ docker info
```

### Step-3 (How to run nginx web application on docker containers)

> First we do pull nginx image from repository server like dockerhub and run container with following configuration parameters like volume, restart policy, port, neme etc.

```bash
[admin@server1 ~]$ docker pull nginx    # Pull docker nginx image
--------------------------------------------------------
# we need to add two 8080 & 8081 tcp port to firewall with admin users sudoers power
[admin@server1 ~]$ sudo firewall-cmd --add-port=8080/tcp --permanent
success
[admin@server1 ~]$ sudo firewall-cmd --add-port=8081/tcp --permanent
success

# Reload firewall-cmd
[admin@server1 ~]$ sudo firewall-cmd --reload
success
--------------------------------------------------------
# now switch to ram user and run nginx web containers
[admin@server1 ~]$ su - ram
ram@dockerserver:~$ docker run --name web-nginx1 -p 8081:80 --restart=always -v vol1:/usr/share/nginx/html -d nginx
6787f299798d6b6d47171e0995d0532ee8bdd352bba6407b561b4e6b7d4400b4

ram@dockerserver:~$ docker run --name web-nginx2 -p 8082:80 --restart=always -v vol1:/usr/share/nginx/html -d nginx
5bcf77f85e4a827579261f7251a7abce698f56f00a1e653fd59caeae677d4c90

ram@dockerserver:~$ ls /var/lib/docker/volumes/vol1/_data/
50x.html  index.html
ram@dockerserver:~$ sudo echo "<h1> This is nginx web container1 </h1>" >> /var/lib/docker/volumes/vol1/_data/index.html

ram@dockerserver:~$ sudo ls /var/lib/docker/volumes/vol2/_data/
50x.html  index.html
ram@dockerserver:~$ sudo echo "<h1> This is nginx web container2 </h1>" >> /var/lib/docker/volumes/vol2/_data/index.html

root@dockerserver:~# docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS          PORTS                                   NAMES
81abf80b6307   nginx     "/docker-entrypoint.…"   9 minutes ago    Up 9 minutes    0.0.0.0:8082->80/tcp, :::8082->80/tcp   web-nginx2
83dec3eeac1c   nginx     "/docker-entrypoint.…"   10 minutes ago   Up 10 minutes   0.0.0.0:8081->80/tcp, :::8081->80/tcp   web-nginx1


ram@dockerserver:~& docker exec -it 81abf80b6307 bash
root@81abf80b6307:/# cat /usr/share/nginx/html/
50x.html    index.html

root@81abf80b6307:/# cat /usr/share/nginx/html/index.html
<h1> This is nginx web container2 </h1>

root81abf80b6307:/# read escape sequence
ram@dockerserver:~# docker exec -it 83dec3eeac1c bash

root@83dec3eeac1c:/# cat /usr/share/nginx/html/index.html
<h1> This is nginx web container1 </h1>
```

> Access web page using Docker server public ip address with 8081 and 8082 port number: Example:
> 
> http://54.175.218.1:8081
> 
> http://54.175.218.1:8082

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699095108368/28c2b4eb-12b5-4922-8223-fdfa253391d2.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699095228353/7787a8f2-2161-499c-902f-b18bc796b816.png align="center")

---

## On Load-Server (34.227.83.161)

### Step-1 (How to configure nginx Load Balancer on "load-server" to distribute trrafic requests load between docker containers on "Docker-Server" )

```bash
$ sudo apt-get update
$ sudo apt-get install nginx
$ sudo systemctl restart nginx
$ sudo systemctl enable nginx
```

```bash
$ sudo vi /etc/nginx/conf.d/load.conf

upstream backend {            # backend is a group name for below mentioned servers 
    server 54.175.218.1:8081;    # Public IP of Docker-Server:port
    server 54.175.218.1:8082;
        }

server {
    listen 80; # You may want to specify the appropriate port    
    server_name 54.175.228.52; # Load-Server public IP (nginx-load-balancer server running on)

location / {
     proxy_pass http://backend;    
        }
    }
```

```bash
$ nginx -t    # to check nginx.conf configuration is correct or not
$ sudo systemctl restart nginx
```

### Step-2 (Check nginx Load-Server to traffic distribution working or not)

> Go to browser and paste : **http://public-ip-of-load-server**
> 
> http://54.175.228.52 and refresh the browser continusely to check

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699114192256/8683fab8-6f21-479f-b227-b5e79ef34f7f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699114220823/96669335-2d42-4357-a4e9-4ec7c6561a6b.png align="center")

---

### Reference:

* Docker setup on ubuntu : [https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)
    
* Manage Docker as a Non-Root User: [https://cloudyuga.guru/hands\_on\_lab/docker-as-non-root-user](https://cloudyuga.guru/hands_on_lab/docker-as-non-root-user)
    
* Nginx Load Balancer Complete Documentation : [https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-to-setup-an-Nginx-load-balancer-example](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/How-to-setup-an-Nginx-load-balancer-example)