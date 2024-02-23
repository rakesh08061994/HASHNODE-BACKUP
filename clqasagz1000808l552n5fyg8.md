---
title: "Unlocking Your Private Web Server to the World for Free: No Cloud Service Fees from AWS, Azure, GCP, and More!"
datePublished: Mon Dec 18 2023 10:39:26 GMT+0000 (Coordinated Universal Time)
cuid: clqasagz1000808l552n5fyg8
slug: unlocking-your-private-web-server-to-the-world-for-free-no-cloud-service-fees-from-aws-azure-gcp-and-more
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1702892960980/1643bb9a-d865-4850-8be0-a6c7929a4c12.png
tags: virtual-machine, docker, ansible, free, kubernetes, cost, setup, vmware, configuration, tunnel, cost-optimisation, bridge

---

If you're feeling frustrated with paying your cloud services bills or if you can't access cloud services because you've used up all your free resources, you're in the right place! We're here to help you out, so no need to worry.

This free service opens up a world of possibilities:

* Showcase your portfolio
    
* Run your blog site locally
    
* Create compatible projects using cloud services
    
* And much more!
    

---

### Step 1:( Build your web application )

Build a web application on your Linux virtual machine and set up web services such as Apache or Nginx.

```plaintext
# yum install -y httpd
# echo "This web server is working" > /var/www/html
# systemctl enable --now httpd ; systemctl status httpd
# firewall-cmd --permanent --add-service=httpd
# firewall-cmd --reload
```

---

### Step 2: Set Up a Tunnel Service to Share Your Content with the Public

```plaintext
# yum install -y npm
# npm install -g localtunnel
# lt --port 80 &
lt --port 80
your url is: https://curvy-books-sneeze.loca.lt
/usr/local/lib/node_modules/localtunnel/bin/lt.js:80
```

This link address is your web application's public address, paste this link to your recruiter, friends, group, or manager so they can see what you shared, or for advanced uses, you can set a reverse proxy instance on the cloud instance, and that instances will listen on port 80 and redirect on this link address. after that, you can set that cloud instance IP to the domain name server.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702895235362/b2badc4d-f789-4d4a-b443-ef73ca31b47a.png align="center")

---

A practical scenario for a big project to save money to spend on cloud resources

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702895391322/bd035508-cc3f-43b7-b317-7f2fb9f32b4e.png align="center")

In this project, all resources are created on a localhost virtual machine for example

* Git ---------&gt; VM Linux (Bridge Network)
    
* Git Gub ---------&gt; Already on the web
    
* Jenkins ------------&gt; VM Linux (Bridge Network)
    
* Docker Hub ----------&gt; Already on the web
    
* <s>AWS --------------------&gt; We are not using it</s>
    
* Kubernetes ----------------&gt; VM Linux (Bridge Network)
    
* Ansible -----------------------&gt; VM Linux (Bridge Network)
    
* Terraform -----------------------&gt; VM Linux (Bridge Network)
    
* Grafana ---------------------------&gt; VM Linux (Bridge Network)
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">On each instance run following command</div>
</div>

```plaintext
# yum install -y npm
# npm install -g localtunnel
# lt --port 80 &
lt --port 80
your url is: https://curvy-books-sneeze.loca.lt
/usr/local/lib/node_modules/localtunnel/bin/lt.js:<App-Port>
```

---

### Reference:-

* `Local tunnel:-` [https://localtunnel.me/](https://localtunnel.me/)