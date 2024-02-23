---
title: "Implementing DevOps Practices: Crafting a Powerful CI/CD Pipeline from Scratch"
datePublished: Thu Dec 07 2023 08:08:32 GMT+0000 (Coordinated Universal Time)
cuid: clpux21hu000508l40bfh8daz
slug: implementing-devops-practices-crafting-a-powerful-cicd-pipeline-from-scratch
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701927456695/4f2fb803-7dbc-42a8-a2ce-94fadeaa657e.png

---

### Introduction:

DevOps is like a team sport for making software better and faster. It's all about teamwork, using cool tools, and working together to make awesome apps and games quickly and with fewer mistakes. In short, DevOps is like teamwork between software developers (who write code) and operations teams (who manage infrastructure). It's a way of working that helps teams build and deliver software more quickly and smoothly. Before starting this project it will be better for us to understand a little some about related terminology and their history.

---

### Before DevOps: ( The Evolution of Application Development )

In the past, developing and delivering software was slow. Teams worked separately, causing delays and communication issues. Everything was done manually, which led to mistakes. Improvements were rare because teams didn't collaborate much, and feedback took a long time to make any changes. This process followed a predefined approach known as SDLC or Software Development Life Cycle.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>What is SDLC? </strong><em>SDLC, or Software Development Life Cycle, is like a roadmap or plan that guides how software is created. It's a step-by-step process that helps teams design, develop, test, and release software in an organized and efficient way</em></div>
</div>

DevOps is also a part of the Software Development Life Cycle (SDLC). It focuses on optimizing and improving the processes within the SDLC, especially in terms of collaboration, automation, and continuous delivery. DevOps practices are integrated into different stages of the SDLC to enhance efficiency, quality, and speed of software development, ensuring a more streamlined and effective development process overall.

Before DevOps, several software development models were commonly used within the broader Software Development Life Cycle (SDLC).:

1. **Waterfall Model:** A linear and sequential approach where each phase (requirements, design, implementation, testing, deployment) is completed before moving to the next. Progression flows in one direction, making it challenging to accommodate changes once a phase is finished.
    
    <div data-node-type="callout">
    <div data-node-type="callout-emoji">💡</div>
    <div data-node-type="callout-text"><em>Once the water starts flowing over the edge of the cliff, it starts falling down the mountain and the water cannot go back up.</em></div>
    </div>
    
    ![Waterfall Model ](https://cdn.hashnode.com/res/hashnode/image/upload/v1701929920660/9680b772-85ed-434e-affa-6d136c588aa7.png align="center")
    
2. **Spiral Model:** An iterative model combining elements of both waterfall and prototyping models. The Spiral Model is a crucial part of the Software Development Life Cycle (SDLC), focusing on managing risks. It resembles a spiral with undefined loops, each loop being a development phase. It involves a series of cycles, each encompassing risk analysis, planning, engineering, and evaluation. It allows for flexibility in accommodating changes during the development process.
    
    ![Spiral Model](https://cdn.hashnode.com/res/hashnode/image/upload/v1701931696953/1f58e452-0a12-41b4-be12-4d48e47697aa.png align="center")
    
3. **Agile Model:** Agile methodologies, such as Scrum or Kanban, emphasize iterative and incremental development. They focus on adaptability, collaboration, and responding to change throughout the development process, allowing for quicker releases and customer feedback incorporation.
    
    **In more simple definition the Agile Model is like building something piece by piece, quickly and flexibly.** **It focuses on teamwork, adapting to changes, and delivering small parts of the project often. Unlike the Waterfall or Spiral Models, Agile doesn't wait until the end to show progress; it's all about quick adjustments and regular updates.**
    
4. **V-Model (Verification and Validation Model):** Similar to the waterfall model but with a focus on validation and verification at each stage. It pairs each development stage with a testing phase, emphasizing testing and validation alongside development activities.
    
5. **Rapid Application Development (RAD):** Emphasizes rapid prototyping and iterative development. It involves close interaction between developers and end-users to quickly build and refine software based on continuous feedback.
    

---

### How to choose : ( Different ways to make software )

1. **Step-by-Step Recipe (Waterfall):** Good when you know exactly what you want, like following steps in order.
    
2. **Adjustable Building Blocks (Agile):** Like playing with Legos, building bit by bit and changing as needed.
    
3. **Risk Management Circles (Spiral):** Handling risks in loops, especially for uncertain or risky projects.
    
4. **Prototypes (Prototype):** Make a sample first, refining it based on feedback before building the whole thing.
    
5. **Little by Little (Incremental):** Working on small parts, adding and improving gradually.
    
6. **Multiple Cycles (Iterative):** Repeating steps to improve with each cycle.
    
7. **All-at-Once (Big Bang):** Building everything together, best for smaller or vague projects.
    

Each way suits different projects depending on how clear the plan is and how much it might change.

---

### DevOps Engineer: (The Role and Responsibilities)

A DevOps engineer is like a bridge builder between software development and IT operations. They work to make sure that the processes for building, testing, and delivering software are smooth and efficient. Their job involves automating tasks, managing tools, and improving collaboration among different teams to speed up software delivery while maintaining quality and reliability. They focus on making sure that the software development and deployment run smoothly and that everyone involved works together effectively.

They rely on a range of tools to accomplish these tasks, including **Jenkins** **Continuous Integration/Continuous Deployment (CI/CD) tools, version control systems like Git, configuration management tools such as Ansible or Puppet, containerization tools like Docker or Kubernetes, monitoring and logging solutions like Prometheus or grafana, collaboration platforms like Slack or Jira, cloud services from providers such as AWS or Azure, as well as testing tools like Selenium or JUnit.** This expansion includes a mention of various tools commonly used by DevOps engineers to support their responsibilities in software development and deployment.

---

### Key Tools Utilized in this Project

Certainly!

1. **Linux:** An open-source operating system used widely due to its stability, security, and flexibility. It's prevalent in server environments and for software development.
    
2. **Git:** A version control system that tracks changes in code, enabling collaboration among developers, and managing codebase versions.
    
3. **GitHub:** A platform built around Git, providing hosting for software development and collaboration using Git repositories.
    
4. **Docker:** Allows the creation, deployment, and running of applications in containers, ensuring consistency across various environments.
    
5. **Kubernetes:** An orchestration tool for managing containerized applications, automating deployment, scaling, and management.
    
6. **DockerHub:** A cloud-based repository where Docker users store and share container images.
    
7. **Jenkins:** An automation server used for Continuous Integration and Continuous Deployment (CI/CD) to automate the software development process.
    
8. **AWS (Amazon Web Services):** A comprehensive cloud computing platform offering various services like computing power, storage, and databases.
    
9. **MobaXterm:** A terminal tool with many features like remote connectivity, X11 server, and tabbed SSH client, enhancing remote working capabilities.
    

![Key Tools Utilized in this Project](https://cdn.hashnode.com/res/hashnode/image/upload/v1701864963941/948020c4-a833-4cb7-a680-b6b1277d111b.png align="center")

---

# Progressing Methodically: ( Our Step-by-Step Approach in this Project )

Throughout this comprehensive DevOps project journey, we will progress through the following steps methodically, one by one.

1. **Set Up GitHub Repository:** Create a GitHub account, establish a code repository, and push the code to it.
    
2. **Provision Jenkins Server:** Set up and configure the Jenkins server for continuous integration and deployment.
    
3. **Deploy Kubernetes Cluster:** Create and configure a Kubernetes cluster for application deployment and management.
    
4. **Build Jenkins CI/CD Pipeline:** Develop a comprehensive CI/CD pipeline using Jenkins for seamless code integration and deployment.
    
5. **Deploy WP-MySQL Galera Multinode:** Implement a robust Galera-based MySQL setup ensuring database security and failover, monitored using Grafana.
    
6. **Configure AWS Load Balancer:** Set up an AWS Application Load Balancer to efficiently distribute traffic between application instances.
    
7. **Domain Name Configuration:** Add a domain name and configure access to the application through it for user-friendly access.
    
8. **Code Verification:** Modify the code and verify the changes to ensure proper functionality.
    
9. **Application Scaling:** Scale the application up and down to handle variable loads efficiently.
    
10. **Rolling Updates & Rollbacks:** Perform rolling updates for seamless application upgrades and have a rollback plan in case of issues.
    
11. **Backup and Restore Strategy:** Implement a backup and restoration process to ensure data security and reliability.
    

---

### Step-1: (**Set Up GitHub Repository)**

Go to the GitHub account [login page](https://github.com/) and log in with your GitHub account authentication. Navigate to [`new`](https://github.com/new) and create a new repository. Assign a Repository name and Description (optional). Choose between the account options: public repositories, visible to the world, and private repositories, requiring payment and authentication for access.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>Create a private GitHub repository that now exists for the free tier</strong>. Free private GitHub repositories have some restrictions placed upon them. One is that no more than three contributors can work on a private GitHub repository.</div>
</div>

[![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701959929281/1c4e2d1b-07f2-4e5b-b5d4-ca7a3ca96535.png align="center")](https://github.com/rakesh08061994/grras)

Check to `Add a README file` That helps write the description for your project. Nevigate to `<> Code` `Local` and copy this `HTTPS` code, actually this link is crucial for pushing new code to your GitHub account repository from git. In my case my repository name is `grras` and HTTPS link is `https://github.com/rakesh08061994/grras.git`

[![Created new repository in GitHub account. ](https://cdn.hashnode.com/res/hashnode/image/upload/v1701960712619/62fab8a5-2748-4c06-a185-0e53d7359192.png align="center")](https://github.com/rakesh08061994/grras)

Further, we will set webhook also for integration with Jenkins for auto build facility in a CI/CD pipeline.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><code>Webhooks</code> allow external services to be notified when certain events happen. When the specified events happen, we’ll send a POST request to each of the URLs you provide.</div>
</div>

[![Webhook: Webhooks allow external services to be notified when certain events happen. When the specified events happen, we’ll send a POST request to each of the URLs you provide.](https://cdn.hashnode.com/res/hashnode/image/upload/v1701961915163/05ddd370-53d6-43f0-aa75-5e8528679121.png align="center")](https://github.com/rakesh08061994/grras/settings/hooks)

When you navigate to `Add webhook` option, you will see a page that needs some configuration to enter manually.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701963823166/d42ff480-8d73-43de-aa55-7a4198f01d9e.png align="center")

---

### Step-2: (**Provision Jenkins Server)**

Either you can go threw this official Jenkins link to [`configure Jenkins on Linux`](https://www.jenkins.io/doc/book/installing/linux/#red-hat-centos) or you can set up your own. For this, we have created a `Rhel Linux` instance and got SSH through [`MobaXterm`](https://mobaxterm.mobatek.net/download.html) on Windows localhost for further configuration and setup. I am using Rhel Linux instance with 4 GB RAM & 2 Core CPU configuration. So let's start.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702456771913/93235730-254e-40b9-b2ab-38f492586eb5.png align="center")

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">I am using Azure Instance here.</div>
</div>

* Follow link [https://www.jenkins.io/doc/book/installing/linux/#red-hat-centos](https://www.jenkins.io/doc/book/installing/linux/#red-hat-centos)
    
    But first change hostname for jenkins machine
    

```plaintext
# hostnamectl set-hostname jenkins
# exec bash
```

* Open the 8080 port on the machine security firewall. You can see 8080 port is listened to by JAVA.
    

```plaintext
# firewall-cmd --permanent --add-port=8080/tcp
# firewall-cmd --reload
# firewall-cmd --list-all
# # netstat -tulpn | grep 8080
tcp6       0      0 :::8080                 :::*                    LISTEN      3648/java
```

* Import a Jenkins repository under `/etc/yum.repos.d` and key from the Jenkins server repository which helps to authenticate that Jenkins should be downloaded or installed from an authenticated source.
    

```plaintext
# wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
# rpm --import https://pkg.jenkins.io/redhat-stable/jenkins.io-2023.key
```

* Upgrade the system
    

```plaintext
# sudo yum upgrade
```

* Install pre-required Jenkins dependencies packages and java sdk, which ismust for Jenkins. Because Jenkins is developed by Oracle and created in java.
    

```plaintext
# yum install fontconfig java-17-openjdk
```

* Install Jenkins in the system
    

```plaintext
# yum install jenkins
```

* Start and enable Jenkins service.
    
* ```plaintext
        # systemctl enable --now jenkins
        # systemctl status jenkins
        
        ● jenkins.service - Jenkins Continuous Integration Server
             Loaded: loaded (/usr/lib/systemd/system/jenkins.service; enabled; vendor preset: disabled)
             Active: active (running) since Tue 2023-12-12 12:07:18 IST; 35min ago
           Main PID: 3648 (java)
              Tasks: 39 (limit: 10756)
             Memory: 359.2M
                CPU: 1min 25.363s
             CGroup: /system.slice/jenkins.service
                     └─3648 /usr/bin/java -Djava.awt.headless=true -jar /usr/share/java/jenkins.war --webroot=/var/cache/jenkins/war --httpPort=8080
        Dec 12 12:07:20 jenkins jenkins[3648]: 2023-12-12 06:37:20.235+0000 [id=49]        INFO        hudson.util.Retrier#start: Performed the action check updates server>
        ...
    ```
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>NOTE:</strong> If you are working with Jenkins in a local VM, then set domain name entry in <code>/etc/hosts</code> file for accessing Jenkins through the domain name. <strong><em>Remember time by time we have to update host entries with other tools machines' IP shortly.</em></strong></div>
</div>

```plaintext
#  echo "192.168.199.139 www.jenkins.com" >> /etc/hosts
```

* Now go to the web browser and paste exactly this.
    

```plaintext
http://www.jenkins.com:8080
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Or if you working with cloud infrastructure, go with Jenkins server public IP address with an 8080 port. Remember &amp; be sure to open the 8080 firewall port in the inbound rule. </div>
</div>

 ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702453246821/1098fc2f-71a1-4184-b516-2d72107989fa.png align="center")

* Unlock Jenkins through Jenkins secret password, which is saved on the location Jenkins home directory `"/var/lib/jenkins/secrets/initialAdminPassword"` copy it and paste into the browser input bar.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702453399883/43d00cbb-4b16-4c49-815b-18a68a952b81.png align="center")

* Click on Default `Install Suggested plugins` option, and wait to complete the installation plugins packages.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702365854608/798cadc8-fb18-41d9-a838-f6cadbea5d10.png align="center")

```plaintext
# cat  /var/lib/jenkins/secrets/initialAdminPassword
557545ee5a8045858f61a3b3ab0ef686
```

* [http://www.jenkins.com:8080/](http://www.jenkins.com:8080/) is your web address to access Jenkins through your local area network. `Click Save and Finish`.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702367111060/140138ae-2319-4623-93bb-603f07b559c2.png align="center")

* Congratulations! Your Jenkins is ready to work.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702453420352/57cdbd02-9a8d-4c8d-99d5-812ccfb356dd.png align="center")

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Important interview questions related to Jenkins.</div>
</div>

<details data-node-type="hn-details-summary"><summary>What is Jenkins? Give a brief introduction</summary><div data-type="detailsContent">Jenkins is an open-source DevOps tool primarily designed for continuous integration/continuous delivery (CI/CD) and deployment. Developed in Java, it serves as automation software used to execute CI/CD workflows commonly referred to as pipelines. Jenkins helps automate various stages of software development, from building and testing code to deploying applications. Jenkins was developed in Java language. and owned by sun microsystem</div></details><details data-node-type="hn-details-summary"><summary>What does CI/CD mean?</summary><div data-type="detailsContent">CI/CD represents two distinct work cultures within Jenkins. 'CI' stands for Continuous Integration, while 'CD' encompasses both Continuous Delivery and Continuous Deployment. This definition might seem a bit tricky, but it's crucial to grasp the concepts of Continuous Integration, Continuous Delivery, and Deployment.</div></details><details data-node-type="hn-details-summary"><summary>what is the actual difference between CI/CD?</summary><div data-type="detailsContent">Think of DevOps as a way of working that's a lot like the journey software goes through from creation to deployment, just with a strong focus on streamlining and automating tasks. It's like connecting a bunch of tools to a central system (like Jenkins) that work together smoothly, forming a clear path for the software to follow. <strong><em>When we talk about Continuous Integration, it means that whenever we make changes to the code, this special system automatically builds and tests it. So, it's like having a buddy who checks your work every time you make a change.</em> </strong>When it's time to share our work with the world, we're really careful about it. Before sending our application out there, we run thorough checks in a special environment that's an exact copy of the real thing, called the staging environment. This helps us ensure that everything works just right before it goes live. That's Continuous Delivery in action. <strong><em>Once everything in the staging area looks good and behaves as expected, we press the button (or sometimes, the system does it for us!) to move our work into the actual environment where everyone can use it. This step is called Continuous Deployment, and it's like the grand finale of the whole process!</em></strong></div></details><details data-node-type="hn-details-summary"><summary>What is the Main difference between Build Periodically &amp; Poll SCM in Jenkins?</summary><div data-type="detailsContent"><em>Poll SCM</em> periodically polls the SCM to check whether changes were made (i.e. new commits) and builds the project if new commits were pushed since the last build. whereas <em>build periodically</em> builds the project periodically even if nothing has changed.</div></details><div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>NOTE: Jenkins Related Information</strong></div>
</div>

```sql
--------> jenkins user is an application user in os check UID:977
# cat /etc/passwd | grep "jenkins"
jenkins:x:977:977:Jenkins Automation Server:/var/lib/jenkins:/bin/false

---------> These following files come with this Jenkins package.
# rpm -ql jenkins
/usr/bin/jenkins
/usr/lib/systemd/system/jenkins.service
/usr/share/java/jenkins.war
/usr/share/jenkins/migrate
/var/cache/jenkins
/var/lib/jenkins

--------> Find all files related to user jenkins and list 
# find / -name jenkins -type d -exec ls -ld {} \;
# find / -name jenkins -type f -exec ls -al {} \;

-------> Check jenkins related files & data
# ls /var/lib/jenkins
config.xml                      jenkins.install.InstallUtil.installingPlugins   jenkins.telemetry.Correlator.xml  plugins                   updates
hudson.model.UpdateCenter.xml   jenkins.install.InstallUtil.lastExecVersion     jobs                              secret.key                userContent
hudson.plugins.git.GitTool.xml  jenkins.install.UpgradeWizard.state             nodeMonitors.xml                  secret.key.not-so-secret  users
identity.key.enc                jenkins.model.JenkinsLocationConfiguration.xml  nodes                             secrets
```

**NOTE:** If you want to change Jenkins's default configuration service then you can modify it with the below command. Follow this official link: [https://www.jenkins.io/doc/book/installing/initial-settings/](https://www.jenkins.io/doc/book/installing/initial-settings/)

```plaintext
# YOURPORT=8080
# PERM="--permanent"
# SERV="$PERM --service=jenkins"

# firewall-cmd $PERM --new-service=jenkins
# firewall-cmd $SERV --set-short="Jenkins ports"
# firewall-cmd $SERV --set-description="Jenkins port exceptions"
# firewall-cmd $SERV --add-port=$YOURPORT/tcp
# firewall-cmd $PERM --add-service=jenkins
# firewall-cmd --zone=public --add-service=http --permanent
# firewall-cmd --reload
```

---

### Step-3: (Set Up Kubernetes Cluster Deployment Environment\*\*)\*\*

* If you are using Cloud Machines like AWS, go with this article: [https://rakeshkumarjangid.hashnode.dev/how-to-setup-kubernetes-cluster-over-cloud-on-ubuntu-os](https://rakeshkumarjangid.hashnode.dev/how-to-setup-kubernetes-cluster-over-cloud-on-ubuntu-os)
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">If you're operating within a Virtual Machine Environment, the rest of the process remains unchanged, with only pre-configuration adjustments required, Follow the article as outlined below</div>
</div>

* Firewall and SELinux should be disabled
    
* swap memory should be removed and off
    

Result of Kubernetes two nodes cluster:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702375570377/451f8253-63d2-4f37-b777-c4b1a33dfe12.png align="center")

Lots of Congratulations...

---

### Step-4: (**Build Jenkins CI/CD Pipeline)**

Your cluster is ready, your Jenkins server is running properly. you have created a GitHub repository account and you are ready to push the code so now we are ready to create a Jenkins pipeline for the application.

**Step4.1: (Push Code on GitHub & add GitHub Jenkins server address on webhook)**

> * A developer writes code using the Windows software application VS Code and pushes it using Git.
>     
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702377249201/7b4a80ea-e318-4842-b8e1-328aa4b128ce.png align="center")
> 
> * Open or edit code through `VS CODE` and push code through `git.`
>     
> 
> ![push code on github](https://cdn.hashnode.com/res/hashnode/image/upload/v1702377579632/22aa3c82-92b2-4124-86eb-8a7f047702ed.png align="center")
> 
> * Add config global information to tell who is actually working and push the code on GitHub repository server.
>     

> ```plaintext
> $ git config --global user.email "jangidrakesh71@gmail.com"
> $ git config --global user.name "Rakesh"
> 
> $ git config user.name
> Rakesh
> 
> $ git config user.email
> jangidrakesh71@gmail.com
> ```
> 
> * Create and move the all data at once using `git checkout -b <new_branch>`
>     
> 
> ```plaintext
> $ git checkout -b stage
> Switched to a new branch 'stage'
> ```
> 
> * Add GitHub remote repository and assign with an alias name `origin` .
>     
> 
> ```plaintext
> $ git status 
> $ git remote add origin https://github.com/rakesh08061994/grras.git
> ```
> 
> * Check whether remote repository are added or not
>     
> 
> ```plaintext
> $ git remote -v
> origin  https://github.com/rakesh08061994/grras.git (fetch)
> origin  https://github.com/rakesh08061994/grras.git (push)
> ```
> 
> <div data-node-type="callout">
> <div data-node-type="callout-emoji">💡</div>
> <div data-node-type="callout-text">We are creating a password less public-key based GitHub authentication</div>
> </div>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702378906887/4ecc1036-9c9a-4c84-ab7f-7671c11c9460.png align="center")

> ```plaintext
> $ ssh-keygen.exe
> $ cat /c/Users/Rakesh-PC/.ssh/id_rsa.pub
> ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQDwOtiIb9Yctu2MJgnS9Avol93dTYGlgPPCaRxTCxz+xxlOb+sZJsz29+4GFkvcZZDbhsmjKRE4ByqlKXBIM+Jv1LlgL8i2hsNFUqdij6Y41kFzbSQIVINNDnQHBOxjMUjz7HRkqteLQQRHRF3roG61sv1kFWC/Xza0DmsHeE6TrRhl+Kj2OEDT7AZ3oQuTp2yGgVTrAk/wOdQnxjvK0eY3EewlVhbJStkCZ6Fac7q05oBh24eY6egf5othVNvUeRq0W5OureB7dyRvobB98rHcmwaLxnzOwZZVH/YHHIgM1PAxCfW3iam+EI9Sm0C++wBZA6/51zzjjekzZaf3Ir04kZe7qZXQoS9hfTDgaW0tanDZvGOl3GdUH9XxnRur5MCNmivcPv8IjlsIleoGM7vLDLXBMTgIEFAZ/++b2MBww59gGQZ6+oCfNgIXBaoGl3FWapbKKx9mbEI1kDxEs11qHvUxTw4kQInacEO6abxvJeI5XFXktvUGokKhBW1P8q8= Rakesh-PC@RakeshPC
> ```
> 
> * We will paste this public key to the GitHub for public key-based authentication.
>     
> * Go to [`https://github.com/settings/keys`](https://github.com/settings/keys) and click on "New ssh key" and paste your public key here.
>     
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702380028918/999f942f-33d3-40a7-9b05-f71a24d4ad56.png align="center")
> 
> Your attached key should reflected like this output, otherwise check your public key and steps carefully.
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702380019407/f174df18-9393-4b2d-bc24-e8d5414b7aa1.png align="center")
> 
> Now open your git on windows, and type below command to check whether we are ready to work with GitHub passwordless.
> 
> * Ensure SSH agent is running on your windows machine
>     
> 
> ```plaintext
> $ eval "$(ssh-agent -s)"
> Agent pid 1217
> ```
> 
> * Add the private key to the SSH agent and check the connection with GitHub.
>     
> 
> ```plaintext
> $  ssh-add ~/.ssh/id_rsa
> $ ssh -T git@github.com
> ```
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702381530104/96de585f-0564-4aab-a1cf-1ef12e8fc9f8.png align="center")
> 
> * Commit the codes with a message, and push them to `stage` branch on `grras` GitHub repository. (This time github will not ask the username and password)
>     
> 
> ```plaintext
> $ git status
> $ git commit -m "This is my first commit"
> $ git push origin stage
> ```
> 
> Output should be
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702381739211/39be5843-7696-480f-a897-6f6cf549ef76.png align="center")
> 
> * Check the data in GitHub repository stage branch .
>     
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702382306525/03f22ea2-d66c-429e-b4cc-28299b69cf74.png align="center")
> 
> * Now add Jenkins to the `GitHub webhook` for trigger option.
>     
> 
> Jenkins-PublicIP/github-webhook/
> 
> ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1702454973118/e92b42cd-5448-446d-a77e-44aa92fb7094.png align="center")

> ---

### Step-5: (**Deploy WP-MySQL Galera Multinode)**

---

### Step-6: (**Configure AWS Load Balancer)**

---

### Step-7: (**Domain Name Configuration)**

---

### Step-8: (**Code Verification)**

---

### Step-9: (**Application Scaling)**

---

### Step-10: (**Rolling Updates & Rollbacks)**

---

### Step-11: (**Backup and Restore Strategy)**

---

### Reference:

* [https://www.makeuseof.com/using-ssh-for-github-passwordless-authentication/](https://www.makeuseof.com/using-ssh-for-github-passwordless-authentication/)