---
title: "How to deploy nginx web-server on the kubernetes cluster and access through a custom domain name. Complete setup on easy Steps."
datePublished: Thu Nov 02 2023 15:02:07 GMT+0000 (Coordinated Universal Time)
cuid: clohbf41n000g0bl4cxjw4zlm
slug: session-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1698937286767/2c351800-1f45-4dcc-a4bc-afc29f6567d5.png

---

I have deployed kubernetes cluster on AWS cloud ec2 instances T2.Medium with 20 GB each storage and 4 GB RAM + 2 Core CPU with Ubuntu OS. I use this link to deploy cluster on ubuntu OS : [https://www.linuxtechi.com/install-kubernetes-on-ubuntu-22-04/](https://www.linuxtechi.com/install-kubernetes-on-ubuntu-22-04/)

So my kubernetes cluster is ready to work. Lets start

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698918127701/6708f9b6-03b8-44f0-bec3-8f3d6c08d896.png align="center")

# Step-1 : (Deploy static web application on Kubernetes Cluster and expose through NodePort.)

### On Master Node (Cluster Node)

```bash
$ kubectl get nodes -o wide
$ mkdir assignment1
$ mkdir -p /home/ubuntu/assignment1/static-data
$ cd /home/ubuntu/assignment1/static-data
$ wget https://www.free-css.com/assets/files/free-css-templates/download/page296/oxer.zip
$ unzip oxer.zip
$ ls oxer-html/
about.html  blog.html  class.html  css  images  index.html  js
```

```bash
$ vi web-app.yml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
  labels:
    app: nginx
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx
        ports:
        - containerPort: 80
        volumeMounts:
        - name: hostpath-volume
          mountPath: /usr/share/nginx/html
      volumes:
      - name: hostpath-volume
        hostPath:
          path: /home/ubuntu/assignment/static-data # static image kept here
```

```bash
$ kubectl create -f webapp.yml
deployment.apps/nginx-deployment created

$ kubectl get pods
NAME                                READY   STATUS    RESTARTS   AGE
nginx-deployment-6d64cb557d-n8rm4   1/1     Running   0          23s
nginx-deployment-6d64cb557d-xp8xd   1/1     Running   0          23s

$ kubectl expose deployment nginx-deployment --name=nginx-deployment-svc --port=80 --target-port=80 --type=NodePort
service/nginx-deployment-svc exposed

$ kubectl get svc
NAME                   TYPE        CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
kubernetes             ClusterIP   10.96.0.1        <none>        443/TCP        6h37m
nginx-deployment-svc   NodePort    10.108.123.135   <none>        80:31046/TCP   4s
```

> Now we will go to AWS deployed kubernetes clusters node and copy public address and paste it to public browser like google chrome

![AWS Cloud setup instances Public IP](https://cdn.hashnode.com/res/hashnode/image/upload/v1698935128992/d2ab38f2-b9ea-48b0-af6a-89f97fad09ac.png align="center")

> So open google chrome broswer:
> 
> Master\_Node\_Public\_Ip:nginx-deployment-svc-port-number
> 
> [http://3.220.236.18:31046/](http://3.220.236.18:31046/)

![http://3.220.236.18:31046/](https://cdn.hashnode.com/res/hashnode/image/upload/v1698935202944/f21113c4-b3ee-4c5d-a293-ce5a2bdcd897.png align="center")

> Till now we deployed our web application on cluster deployment servers. Now we have to require setup reverse-proxy, so we can access our web-app without specifying portnumber like 31046. so lets setup nginx reverse proxy for this.

> ### Create a new AWS instance as an nginx-reverse-proxy server for specifying reverse proxy setup
> 
> ---

# Step-2 (On nginx server (A new aws instance for reverse proxy))

```bash
$ sudo apt-get update 
$ sudo apt-get install nginx
$ sudo systemctl restart nginx
$ sudo systemctl enable nginx
$ sudo cd /etc/nginx/conf.d

$ sudo vi nginx.conf
server {
    listen 80; # will listen app ipv4 and ipv6 address on port number 80
    listen [::]:80;

    server_name 3.90.48.34; # Public IP of nginx-server

    location / {
        proxy_pass http://3.220.236.18:31046/;  # public ip of clusters master node ip and nodeport


$ sudo nginx -t   # check .conf file vaildation
nginx: the configuration file /etc/nginx/nginx.conf syntax is ok
nginx: configuration file /etc/nginx/nginx.conf test is successful

$ sudo nginx -s reload    # reload file
$ sudo systemctl restart nginx    # reload nginx server
```

> Now we setup nginx server completly. So take nginx-server public ip from aws console and paste it on chrome broser:
> 
> http://[3.90.48.34](http://3.90.48.34)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698936491813/5a8983ce-bee5-49cd-8bd8-5ae6037ff2e7.png align="center")

### And reverse proxy setup works properly

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698936740582/757004bd-6166-4b01-8f8a-648fac328518.png align="center")

---

# Step - 3 (How to access our cluster web-server through domain name insted of servers public IP.)

### For Example:- http://www.website.com

> For this we have to require to purchase a domain name, like godaddy, hostinger, google domain, namecheap, bigrock etc. there are lots of option out there but here i am choosing namecheap domain registrar service.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1698996387690/7d47a328-3b5b-45bf-b1e7-ccaa2b203e71.png align="center")

As you see i have purchased a domain name "rakamodify.online" from namecheap domain registrar. Now you have to setup DNS nameserver and access public ip to domain name. I go to "advance DNS option" &gt; Host Record &gt; Add new record.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699013379660/08b3ed9d-b4a5-4ca6-bcf7-8ab93cdb1ce1.png align="center")

> Note: we have to update our nginx-proxy configuration file with some changes
> 
> ```bash
> $ sudo vi nginx.conf
> server {
>     listen 80; # will listen app ipv4 and ipv6 address on port number 80
>     listen [::]:80;
> 
>     server_name www.rakamodify.online ; # Insted of 3.90.48.34 Public IP of nginx-server, we use domain name    
>     location / {
>         proxy_pass http://3.220.236.18:31046/;  # public ip of clusters master node ip and nodeport
> 
> $ sudo systemctl restart nginx
> ```

![Web application access by domain name insted of public IP](https://cdn.hashnode.com/res/hashnode/image/upload/v1699013378985/a0ea157d-50ee-4119-a891-d3eceb42a0a4.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1699014827608/2ebf7f71-78e1-4bbd-9c02-f7e2dc623410.png align="center")

---

### Reference:

* **How to setup Kubernetes Cluster on Ubuntu OS:** [https://www.linuxtechi.com/install-kubernetes-on-ubuntu-22-04/](https://www.linuxtechi.com/install-kubernetes-on-ubuntu-22-04/)
    
* **static website content**: [https://www.free-css.com/free-css-templates/page296/oxer](https://www.free-css.com/free-css-templates/page296/oxer)
    
* **How to set reverse proxy:** [https://www.youtube.com/watch?v=B62QSbPhh1s](https://www.youtube.com/watch?v=B62QSbPhh1s)
    
* **How to add an A host record for a domain name in Namecheap account** [https://](https://www.youtube.com/watch?v=tQ2UALMOs9w)[www.youtube.com/watch?v=qjnQvuHqjxM](http://www.youtube.com/watch?v=qjnQvuHqjxM)
    
* **namecheap conect domain to server :** [https://www.namecheap.com/support/knowledgebase/article.aspx/9837/46/how-to-connect-a-domain-to-a-server-or-hosting/](https://www.namecheap.com/support/knowledgebase/article.aspx/9837/46/how-to-connect-a-domain-to-a-server-or-hosting/)
    
* To check & resolve DNS : [https://www.dnswatch.info/](https://www.dnswatch.info/)