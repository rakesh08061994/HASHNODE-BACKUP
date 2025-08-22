---
title: "GitLab CICD Learning Project-1"
seoTitle: "GitLab CICD java maven build test deploy project with notification"
datePublished: Fri Aug 22 2025 16:02:14 GMT+0000 (Coordinated Universal Time)
cuid: cmen0qrxq001p02jp7rv38dx9
slug: gitlab-cicd-learning-project-1
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1755878317124/249e6202-32ab-43bd-bf2a-a0bd1b30d667.png
tags: aws, projects, freelancing, devops, gitlab, gitlab-ci, gitlab-runner, devops-articles, devops-trends, devops-journey, gitlab-ssh, devopscommunity, gitlab-cicd

---

> *Most of the time in their life, people find themselves lost, lazy, and waiting for someone else to help them out of the darkness. But the truth is—strength comes from within. We rise when we decide to take that first step forward.*
> 
> *Every big journey begins with a small step. I believe that even small progress is still progress. Fear and laziness may try to stop us, but discipline and consistency always win. What truly matters is starting, and then moving forward—step by step—with confidence and purpose.*
> 
> *With this mindset, I’m beginning to share my learnings through this blog. The tool I recently started exploring is* ***\[Tool Name\]****, and in this post, I’ll walk you through what I’ve discovered, how I practiced it, and why it can add real value.*

---

In this blog we are going to create a GitLab project, that will showcase the skillset regarding GitLab tool.  
So project will look like this

# Open your GitLab account

# Create a Group and a project within

You can create a group, directly go to **“New group“** button, there you will see two ways to create group, but you need to create a group by click on **“Create Group“** . Give him a name and done, you have successfully created a group. In GitLab, your group is like user account in GitHub, ex: **GitHub-username**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755861555972/27535335-1216-4dac-8c65-b9a0f01a4268.png align="center")

Now in this group, you have to create project by pressing “New Project“ button exact same way of group creation. This is like repository in your GitHub account.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755861581906/44502f55-a92f-4441-9675-3743201eadf1.png align="center")

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">We are using <strong>“GitLab-project1“ </strong>project this time.</div>
</div>

# Push your application data to project

As a developer you need to push all the project code from your system to GitLab project using Git Tool.

Here i have pushed all the project code in **master branch.**

Link: [https://gitlab.com/devrakaops1/java-todo-app-cicd/-/tree/master?ref\_type=heads](https://gitlab.com/devrakaops1/java-todo-app-cicd/-/tree/master?ref_type=heads)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755862246079/bc383308-c85c-41c5-8952-e22b8272f1e7.png align="center")

# Add a Runner

now this time your next work is to create a EC2-Instance that we can use as a GitLab custom Runner to run our project.

Step-1: Go to your AWS account and create an ec2-instance with t2.medium and rhel-9 OS

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755862925720/5397bcc0-c0ea-4c0d-b7a2-3c9b1205852c.png align="center")

Step-2: Take SSH to the instance and run provided commands to make them GitLab Runner

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755863213985/a9e22ea0-ce0f-4770-9436-aee157d6c386.png align="center")

Now run commands to became GitLab Runner

Go to settings &gt; CICD &gt; Runners &gt; Create Project Runner

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755864605786/55eb9eb5-3614-42a2-bbf0-e1122ca8cd6b.png align="center")

And click on “Create Runner“

Now select your OS “RedHat Linux“ in my case.  
Now you have to run some commands but GitLab Runner must be installed before you can register a runner. For this run below commands by clicking in link “[How do I install GitLab Runner?](https://gitlab.com/devrakaops1/java-todo-app-cicd/-/runners/49575617/register#)“

Select your architecture of system, run the following commands.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755864678249/9ef8abcc-2321-4a4e-aeb3-dacb06c99852.png align="center")

But don’t forgot to run command “**yum update**“. This will save your time and to lots of confusions.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755864780447/ec778d83-2713-4d66-9366-982d6fc07ac3.png align="center")

And then following command.

```yaml
 gitlab-runner register --url https://gitlab.com --token glrt-oxwG1lduWEnIh3DJiwHCqm86MQpwOjE3ZmVkeQp0OjMKdTpobDhpbRg.01.1j0181m9p
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755865369666/99500a40-e61a-447c-a3d1-96726c489519.png align="center")

Now check your runner is working and active

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755865538378/ae3c0d53-7093-4834-b106-d8d327618e9c.png align="center")

make sure you have turn off GitLab default runner

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755865577159/6925dda9-5162-4371-afe9-58fc299c2cf1.png align="center")

Now your runner is active and in working state. Later you can mention this runner using mentioning tags “dev“ in main CICD file `.gitlab-ci.yml`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755865703719/5a45f314-c070-4e65-8342-5729dc725c29.png align="center")

# Add Docker Credentials Variables

To add variable in GitLab, go to settings &gt; CICD &gt; Variables &gt; add variable

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755865819597/7677858e-cb14-4189-9da9-f9bf3a9a1df8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755865866717/2fe0238f-b08c-4d2d-ae73-28bd831ae952.png align="center")

We have to create two variable:

```yaml
DOCKERHUB_NAME = ********
DOCKERHUB_PASS = *****************************
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755865783709/4d77182b-1725-4879-b02d-14c0f2d568e0.png align="center")

Now its time to create CICD file. Name should be “`.gitlab-ci.yml`“

# Create a GitLab CICD file

```yaml
stages:
        - build
        - test
        - push_to_dockerhub
        - deploy
variables:
        NAME: "Rakesh"
        CITY: "Jaipur"

build_job:
        stage: build
        script:
                - echo "$CI_JOB_STAGE is working in $CI_COMMIT_BRANCH branch"
                - docker build -t todo-app:latest .
        tags:
                - dev

test_job:
        stage: test
        script:
                - echo "$CI_JOB_STAGE is working in $CI_COMMIT_BRANCH branch"
                - docker image ls
        tags:
                - dev

push_job:
        stage: push_to_dockerhub
        before_script: 
                - docker login -u $DOCKERHUB_NAME -p $DOCKERHUB_PASS  
        script:
                - echo "$CI_JOB_STAGE is working in $CI_COMMIT_BRANCH branch"              
                - docker image tag todo-app:latest      $DOCKERHUB_NAME/todo:latest
                - docker push $DOCKERHUB_NAME/todo:latest
        tags:
                - dev

deploy_job:
        stage: deploy
        script:
                - echo "$CI_JOB_STAGE is working in $CI_COMMIT_BRANCH branch"
                - docker compose up -d
                - echo "Working Successful"
        tags:
                - dev
```

# Install Docker in Ec2 Instance

Install docker: [https://docs.docker.com/engine/install/centos/](https://docs.docker.com/engine/install/centos/)

```bash
systemctl enable --now docker
```

# Configuration Work

```bash
yum install -y git
echo "gitlab-runner  ALL=(ALL)   NOPASSWD:ALL" > /etc/sudoers.d/gitlab-runner
```

# Check the CICD pipeline

When you pushes the code to the repository server in master branch, automatically cicd pipeline will trigger.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755876186416/832e9e9f-a917-43a8-a054-ce092bfe0fa1.png align="center")

Go to build &gt; pipeline &gt;

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755876388643/76a58763-ef68-4edc-82c0-4ceda13739b3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755876665408/2ae7e9e6-fd62-4819-ac70-8359d424897c.png align="center")

If you want to see on instance, there is docker container is running on port 8000.  

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755876731152/c6b44f1d-d22f-46fd-95bb-26510ef132f2.png align="center")

So we have to add 8000 inbound port to the AWS EC2-Instances security group

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755876836634/25b49cb6-0d61-482a-a80b-3f86b5c237a0.png align="center")

# Access the application

Because we have deployed application on ec2-instance so will see the output using instances public IP with appending 8000 port on web browser.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1755877118878/50c92c42-a637-4d82-8e61-9767788a5c52.png align="center")

# Output Logs

* Build\_job
    
    ```json
    Running with gitlab-runner 18.3.0 (9ba718cd)
      on gitlab-runner1 jHBjwSbnw, system ID: s_5da8ab1e406d
    Preparing the "shell" executor
    00:00
    Using Shell (bash) executor...
    Preparing environment
    00:00
    Running on ip-172-31-95-28.ec2.internal...
    Getting source from Git repository
    00:01
    Gitaly correlation ID: 089ad318cb6440518c7c06d9f9afc0ee
    Fetching changes with git depth set to 20...
    Reinitialized existing Git repository in /builds/jHBjwSbnw/0/devrakaops1/java-todo-app-cicd/.git/
    Checking out 65f03dd9 as detached HEAD (ref is master)...
    Skipping Git submodules setup
    Executing "step_script" stage of the job script
    00:08
    $ echo "Hello my name is $NAME and i lived in $CITY"
    Hello my name is Rakesh and i lived in Jaipur
    $ echo "$CI_JOB_STAGE is working in $CI_COMMIT_BRANCH branch"
    build is working in master branch
    $ echo pwd
    pwd
    $ echo whoami
    whoami
    $ echo ls -al
    ls -al
    $ docker build -t todo-app:latest .
    #0 building with "default" instance using docker driver
    #1 [internal] load build definition from Dockerfile
    #1 transferring dockerfile: 297B done
    #1 DONE 0.0s
    #2 [auth] library/node:pull token for registry-1.docker.io
    #2 DONE 0.0s
    #3 [internal] load metadata for docker.io/library/node:12.2.0-alpine
    #3 DONE 0.2s
    #4 [internal] load .dockerignore
    #4 transferring context: 2B done
    #4 DONE 0.0s
    #5 [1/5] FROM docker.io/library/node:12.2.0-alpine@sha256:2ab3d9a1bac67c9b4202b774664adaa94d2f1e426d8d28e07bf8979df61c8694
    #5 DONE 0.0s
    #6 [internal] load build context
    #6 transferring context: 15.71kB done
    #6 DONE 0.0s
    #7 [2/5] WORKDIR /node
    #7 CACHED
    #8 [3/5] COPY . .
    #8 DONE 0.0s
    #9 [4/5] RUN npm install
    #9 0.710 npm WARN read-shrinkwrap This version of npm is compatible with lockfileVersion@1, but package-lock.json was generated for lockfileVersion@2. I'll try to do my best with it!
    #9 5.604 
    #9 5.604 > ejs@2.7.4 postinstall /node/node_modules/ejs
    #9 5.604 > node ./postinstall.js
    #9 5.604 
    #9 5.653 Thank you for installing EJS: built with the Jake JavaScript build tool (https://jakejs.com/)
    #9 5.653 
    #9 5.909 npm WARN my-todolist@0.1.0 No repository field.
    #9 5.910 npm WARN my-todolist@0.1.0 No license field.
    #9 5.910 
    #9 5.913 added 291 packages from 653 contributors and audited 291 packages in 5.249s
    #9 5.914 found 33 vulnerabilities (10 low, 3 moderate, 16 high, 4 critical)
    #9 5.914   run `npm audit fix` to fix them, or `npm audit` for details
    #9 DONE 6.1s
    #10 [5/5] RUN npm run test
    #10 0.428 
    #10 0.428 > my-todolist@0.1.0 test /node
    #10 0.428 > mocha --recursive --exit
    #10 0.428 
    #10 0.624 
    #10 0.625 
    #10 0.627   Simple Calculations
    #10 0.628 This part executes once before all tests
    #10 0.628     Test1
    #10 0.628 executes before every test
    #10 0.629       ✓ Is returning 5 when adding 2 + 3
    #10 0.629 executes before every test
    #10 0.630       ✓ Is returning 6 when multiplying 2 * 3
    #10 0.630     Test2
    #10 0.630 executes before every test
    #10 0.630       ✓ Is returning 4 when adding 2 + 3
    #10 0.630 executes before every test
    #10 0.630       ✓ Is returning 8 when multiplying 2 * 4
    #10 0.631 This part executes once after all tests
    #10 0.631 
    #10 0.631 
    #10 0.631   4 passing (7ms)
    #10 0.631 
    #10 DONE 0.6s
    #11 exporting to image
    #11 exporting layers
    #11 exporting layers 1.1s done
    #11 writing image sha256:c210dbc115207b92008265a12fe9e3059e2b259a59627ce44805f917bb2c49dd done
    #11 naming to docker.io/library/todo-app:latest done
    #11 DONE 1.1s
    Cleaning up project directory and file based variables
    00:00
    Job succeeded
    ```
    
* test\_job
    
    ```json
    Running with gitlab-runner 18.3.0 (9ba718cd)
      on gitlab-runner1 jHBjwSbnw, system ID: s_5da8ab1e406d
    Preparing the "shell" executor
    00:00
    Using Shell (bash) executor...
    Preparing environment
    00:00
    Running on ip-172-31-95-28.ec2.internal...
    Getting source from Git repository
    00:01
    Gitaly correlation ID: 14a70c8d29bf4a60bb71afd99d959466
    Fetching changes with git depth set to 20...
    Reinitialized existing Git repository in /builds/jHBjwSbnw/0/devrakaops1/java-todo-app-cicd/.git/
    Checking out 65f03dd9 as detached HEAD (ref is master)...
    Skipping Git submodules setup
    Executing "step_script" stage of the job script
    00:00
    $ echo "$CI_JOB_STAGE is working in $CI_COMMIT_BRANCH branch"
    test is working in master branch
    $ docker image ls
    REPOSITORY         TAG       IMAGE ID       CREATED         SIZE
    todo-app           latest    c210dbc11520   5 seconds ago   104MB
    [MASKED]/todo   latest    5970356deaa0   3 minutes ago   104MB
    Cleaning up project directory and file based variables
    00:00
    Job succeeded
    ```
    
* push\_to\_dockerhub\_job
    
    ```json
    Running with gitlab-runner 18.3.0 (9ba718cd)
      on gitlab-runner1 jHBjwSbnw, system ID: s_5da8ab1e406d
    Preparing the "shell" executor
    00:00
    Using Shell (bash) executor...
    Preparing environment
    00:00
    Running on ip-172-31-95-28.ec2.internal...
    Getting source from Git repository
    00:01
    Gitaly correlation ID: 4cfb3d55ef244d9dad1a96d22cdd7691
    Fetching changes with git depth set to 20...
    Reinitialized existing Git repository in /builds/jHBjwSbnw/0/devrakaops1/java-todo-app-cicd/.git/
    Checking out 65f03dd9 as detached HEAD (ref is master)...
    Skipping Git submodules setup
    Executing "step_script" stage of the job script
    00:04
    $ echo "$CI_JOB_STAGE is working in $CI_COMMIT_BRANCH branch"
    push_to_dockerhub is working in master branch
    $ docker login -u $DOCKERHUB_NAME -p $DOCKERHUB_PASS
    WARNING! Using --password via the CLI is insecure. Use --password-stdin.
    Login Succeeded
    $ docker image tag todo-app:latest      $DOCKERHUB_NAME/todo:latest
    $ docker push $DOCKERHUB_NAME/todo:latest
    The push refers to repository [docker.io/[MASKED]/todo]
    b4a20abeed57: Preparing
    b5a342a444fe: Preparing
    2630b0641421: Preparing
    48568d6a9c95: Preparing
    917da41f96aa: Preparing
    7d6e2801765d: Preparing
    f1b5933fe4b5: Preparing
    7d6e2801765d: Waiting
    f1b5933fe4b5: Waiting
    48568d6a9c95: Layer already exists
    917da41f96aa: Layer already exists
    7d6e2801765d: Layer already exists
    f1b5933fe4b5: Layer already exists
    b4a20abeed57: Pushed
    2630b0641421: Pushed
    b5a342a444fe: Pushed
    latest: digest: sha256:c289ae82475448c92ba2db4d00584f9664fdc9bc300208a44dbc7c878c6623c0 size: 1785
    Cleaning up project directory and file based variables
    00:01
    Job succeeded
    ```
    
* deploy\_job
    
    ```json
    Running with gitlab-runner 18.3.0 (9ba718cd)
      on gitlab-runner1 jHBjwSbnw, system ID: s_5da8ab1e406d
    Preparing the "shell" executor
    00:00
    Using Shell (bash) executor...
    Preparing environment
    00:00
    Running on ip-172-31-95-28.ec2.internal...
    Getting source from Git repository
    00:01
    Gitaly correlation ID: 45752bebf3ae4b6582bb25bdff2e7ac4
    Fetching changes with git depth set to 20...
    Reinitialized existing Git repository in /builds/jHBjwSbnw/0/devrakaops1/java-todo-app-cicd/.git/
    Checking out 65f03dd9 as detached HEAD (ref is master)...
    Skipping Git submodules setup
    Executing "step_script" stage of the job script
    00:01
    $ echo "$CI_JOB_STAGE is working in $CI_COMMIT_BRANCH branch"
    deploy is working in master branch
    $ docker compose up -d
    time="2025-08-22T15:30:00Z" level=warning msg="/builds/jHBjwSbnw/0/devrakaops1/java-todo-app-cicd/docker-compose.yaml: the attribute `version` is obsolete, it will be ignored, please remove it to avoid potential confusion"
     Network java-todo-app-cicd_default  Creating
     Network java-todo-app-cicd_default  Created
     Container java-todo-app-cicd-web-1  Creating
     Container java-todo-app-cicd-web-1  Created
     Container java-todo-app-cicd-web-1  Starting
     Container java-todo-app-cicd-web-1  Started
    $ echo "Working Successful"
    Working Successful
    Cleaning up project directory and file based variables
    00:00
    Job succeeded
    ```
    

---

Thank you

GitLab repo: [https://gitlab.com/devrakaops1/java-todo-app-cicd/-/tree/master?ref\_type=heads](https://gitlab.com/devrakaops1/java-todo-app-cicd/-/tree/master?ref_type=heads)

Linkedin: [https://www.linkedin.com/in/rakeshkumarjangid/](https://www.linkedin.com/in/rakeshkumarjangid/)