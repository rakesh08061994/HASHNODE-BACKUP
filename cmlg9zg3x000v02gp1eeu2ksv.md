---
title: "Kubernetes Deployment Strategies Explained: Recreate, RollingUpdate, Blue–Green & Canary"
seoTitle: "Kubernetes Deployment Strategies Overview"
seoDescription: "Explore Kubernetes deployment strategies: Recreate, RollingUpdate, Blue-Green, and Canary for safe application updates with minimal disruption"
datePublished: Tue Feb 10 2026 07:24:28 GMT+0000 (Coordinated Universal Time)
cuid: cmlg9zg3x000v02gp1eeu2ksv
slug: kubernetes-deployment-strategies-explained-recreate-rollingupdate-bluegreen-and-canary
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1770707943642/6de4de51-119b-4e8f-855f-7bd178c67048.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1770708166484/970defbf-c091-4115-b499-bdcfd4c9bcd4.png
tags: kubernetes, devops, devops-articles, recreate, canary-deployment, deployment-strategies, rollingupdates

---

Hello Geeks,

This is **Rakesh**, and once again, I am here with another **deep, honest, and real-world learning** related to **Kubernetes**. Today’s topic is **Kubernetes Deployment Strategy**.

I want you to read this documentation **slowly**, like personal notes written in a notebook. This is not copied content, not interview-only material, and not something you just skim. This is written so that **you feel how deployment actually happens inside a company**, why certain decisions are taken, and how Kubernetes behaves behind the scenes.

My goal is simple: after reading this, you should be able to **explain deployment strategies confidently to anyone**, and also **implement them practically**.

---

Let us first understand what we really mean by the term **deployment strategy**.

In real life, deployment strategy is not a Kubernetes keyword first. It is a **business and engineering problem**. Whenever a company is running an application that users are actively using, the company cannot just stop everything and start again. Users may be making payments, booking tickets, logging in, or consuming services. Even a few seconds of downtime can break user trust, create financial loss, or damage reputation.

So whenever a company says, “We want to upgrade our application from an old version to a new version,” the next question is never *how to deploy*, but always *how to deploy safely*.

That safe and planned way of upgrading an application from one version to another is called a **deployment strategy**.

In very simple language: Deployment strategy means **the method we choose to replace the old running application with a new version, without breaking the system**.

Kubernetes comes into the picture as the system that executes this plan for us.

---

Now comes one of the most important truths that every Kubernetes learner must clearly understand.

As per **official Kubernetes documentation**, Kubernetes supports **only two deployment strategies by default**:

Recreate and RollingUpdate.

That’s it. Nothing more.

Many people believe that Blue-Green and Canary are also default Kubernetes deployment strategies, but that belief is **incomplete and slightly incorrect**. Blue-Green and Canary are **deployment patterns**, not native strategies. Kubernetes does not give you a direct field called `type: BlueGreen`. Instead, Kubernetes gives you building blocks like Deployments, Services, labels, selectors, and controllers. Using these building blocks, engineers design advanced patterns like Blue-Green and Canary.

These patterns exist because the default strategies have **real limitations**, especially in production environments.

So to truly understand Blue-Green, we must start from the beginning — from the simplest strategy.

---

1. ## **Let us start with the Recreate Deployment Strategy.**
    

Recreate is the most basic and straightforward strategy. Its behavior is very simple. When a new version of the application needs to be deployed, Kubernetes first **terminates all existing Pods** of the application. Only after all old Pods are terminated does Kubernetes start creating new Pods with the updated version.

This means there is a clear gap between stopping the old application and starting the new one.

That gap is called **downtime**.

Downtime is not an accidental side effect here. Downtime is the **natural and unavoidable result** of how Recreate works.

Now let us imagine a real company scenario.

Suppose there is a payment-related company. The application is already running smoothly. The frontend is serving users, the backend is connected to the database, APIs are responding correctly, and users are happily making transactions. Behind the scenes, Kubernetes is managing Deployments, Services, Secrets, ConfigMaps, and storage. Everything is stable.

Now the manager comes to the tech team and says: “Can we upgrade the frontend UI to a newer version?”

If the DevOps team uses the Recreate strategy, Kubernetes will first stop all existing frontend Pods. During this time, the Service has no Pods to send traffic to. Users will see errors, blank pages, or timeouts. Only after the new Pods start and become ready will the application be available again.

So even if the downtime is small, downtime **will definitely happen**.

This is why the Recreate strategy is not trusted for production user-facing applications.

## Now, let us make this learning REAL — Practical part for each deployment strategy

Till now, we understood the *why* and *what*. Now we will move to the *how*. This section is written so that **you can sit in front of a laptop and actually do it**, not just imagine it.

I will explain the practical part **slowly**, and assuming you have enough learning of Kubernetes, honestly, not rushing.

---

## Practical: Recreate Deployment Strategy

First, we intentionally use Recreate so that you **personally observe why it is risky**.

Create a simple Deployment using nginx. This will act as our frontend application.

```yaml
# vim recreate_deployment.yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: recreate-deployment
  labels:
    policy: recreate
spec:
  replicas: 10
  selector:
    matchLabels:
      app: recreate 
  template:
    metadata:
      labels: 
        app: recreate
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
```

```bash
kubectl create -f recreate_deployment.yml -n strategy
```

Note: For my safe practice purposes, I am using a namespace, so all resources are kept aligned in one location.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770290857919/9d53e3d6-5450-4b94-87c3-a38e5433ef44.png align="center")

Now create a NodePort service for this deployment, so users can request publicly to the application using the service.

```yaml
# vim recreate_Service.yml

apiVersion: v1
kind: Service
metadata:
  name: recreate-service
spec:
  type: NodePort
  selector:
    app: recreate
  ports:
    - port: 80
      # By default and for convenience, the `targetPort` is set to
      # the same value as the `port` field.
      targetPort: 80
      # Optional field
      # By default and for convenience, the Kubernetes control plane
      # will allocate a port from a range (default: 30000-32767)
      nodePort: 30007
```

Now create both resources.

```yaml
# kubectl create -f recreate_Service.yml -n strategy
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770291205353/2ffef890-3695-47cf-90f9-cb965d6e2c61.png align="center")

Apply both manifests and access the application.

At this stage, everything works normally.

Now we are going to update the pre-exist Deployment image to other version ex:`nginx:1.25` and apply it again. You can edit existing running deployment using following method:

1. Direct EDIT method `kubectl edit deployment`
    
2. Using `kubectl patch`
    
3. Using `kubectl set image`
    
4. Edit deployment and apply changes using `kubectl create -f`
    

```yaml
kubectl set image deployment/recreate-deployment nginx=nginx:1.25.0 -n strategy
```

You will observe that all pods 100 % get down first, and new pods spin out after a few seconds. This is called downtime, and this is an issue.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770291842119/dca1bb9e-8369-4e00-b1e1-a8c2bf6c830b.png align="center")

Later, check again and see there are all the new pods are running. Which means there are two ReplicaSet is available for this deployment with two versions. One for the old version `nginx:1.14.2` and second one for new version `nginx:1.25.0` . This process of being updated with a newer version is called rolling update, even this is for Recreate strategy.

```bash
kubectl get pods -n strategy
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770291878472/ff13558b-11fd-46a8-a706-6af72b97e17e.png align="center")

Check ReplicaSet status.

```bash
kubectl get all -n strategy
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770292231511/fde20869-e9ce-4c26-b0ec-ee963c43e502.png align="center")

See, there is a deployment running two `ReplicaSet` with different versions.

---

### Conclusion of the Recreate Deployment Strategy

So, the Recreate strategy still has its place. It is useful for proof-of-concept environments, internal testing, development setups, and batch-style workloads where downtime does not matter. But for real production systems, Recreate is almost never acceptable.

**This limitation of Recreate naturally led engineers to ask a better question:**

“Can we update the application without stopping everything at once?”

That question gave rise to the **RollingUpdate strategy**.

---

2. ## RollingUpdate is the default strategy in Kubernetes, and it is much smarter than Recreate.
    

Instead of stopping all Pods together, RollingUpdate replaces Pods **gradually**. Some old Pods continue running while new Pods are being created. This way, the application usually remains available during the update process. Between updating the pods version, it takes some time to get back ready to serve the application publicly. Read this for more [Pods Termination Behavior](https://kubernetes.io/docs/tutorials/services/pods-and-endpoint-termination-flow/) .

```bash
vim rolling_update_deployment.yml

apiVersion: apps/v1
kind: Deployment
metadata:
  name: rolling-update-deployment
  labels:
    app: nginx
spec:
  replicas: 10
  selector:
    matchLabels:
      app: rolling-update
  strategy:
   type: RollingUpdate
   rollingUpdate:
     maxUnavailable: 0           # High Availability 
     maxSurge: 2                  # Two extra pods will create in advance
  template:
    metadata:
      labels:
        app: rolling-update
    spec:
      terminationGracePeriodSeconds: 10 # extra long grace period
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80
```

And expose the deployment with a service NodePort.

```bash
vim rolling_update_service.yml

# vim recreate_Service.yml

apiVersion: v1
kind: Service
metadata:
  name: rolling-update-service
spec:
  type: NodePort
  selector:
    app: rolling-update
  ports:
    - port: 80
      # By default and for convenience, the `targetPort` is set to
      # the same value as the `port` field.
      targetPort: 80
      # Optional field
      # By default and for convenience, the Kubernetes control plane
      # will allocate a port from a range (default: 30000-32767)
      nodePort: 30010
```

Now create resources using commands.

```bash
kubectl create -f rolling_update_deployment.yml -n strategy
kubectl create -f rolling_update_deployment.yml -n strategy
kubectl get all -n strategy
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770294714560/10014a1f-568e-4c0e-b674-4d0246ea9c85.png align="center")

Now change the version of deployment pods.

From old to new version and apply changes to the existing deployment.

```bash
kubectl set image deployment/rolling-update-deployment nginx=nginx:1.25.0 -n strategy
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770294908716/95d64d8b-35a2-498e-984d-84573870e36b.png align="center")

At first glance, the RollingUpdate strategy seems ideal. It offers no downtime, a smooth transition, and a controlled rollout. With `maxSurge: 2`, two extra pods are created first, and then old pods are deleted until all pods are updated to the new version. What else do we need?

Right ????

While the RollingUpdate strategy ensures high availability, the issue is not just about availability. The real problem is that, **for a brief moment, the application runs two versions simultaneously.** This means some users might be using the older version while others are on the newer version. This can lead to compatibility issues between the backend and frontend, causing potential disconnects. Therefore, this approach may not be entirely reliable for production-level work.

Running two versions at the same time, even for a few seconds, can be risky. Downtime, no matter how brief, can impact a company in terms of money, time, and trust.

Now let us go back to the real-world company example.

> Suppose the frontend version v1 is fully compatible with the backend APIs and database. Everything works fine. Now a new frontend version v2 is built. The UI is improved, performance is enhanced, but v2 expects some new API responses or slightly different behavior from the backend.

> During a RollingUpdate, both frontend v1 and frontend v2 are running together. Some users hit v1 and everything works. Some users hit v2, and suddenly they see errors because the backend does not yet support those expectations.

> This creates an inconsistent user experience.

It is very important to understand that Kubernetes is not wrong here. Kubernetes is doing exactly what RollingUpdate promises. The real problem is that RollingUpdate **allows mixed-version traffic**.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>“This mixed state is the core limitation of RollingUpdate.”</strong></div>
</div>

RollingUpdate cannot guarantee that all users will see only one version at a time.

And for some businesses, especially high-risk systems like payments, banking, authentication, or compliance-heavy applications, this risk is unacceptable.

That is why companies needed something even safer.

---

3. ## This is where the **Blue-Green Deployment pattern** comes into the picture.
    

Blue-Green deployment is not about replacing Pods. It is about **switching traffic**.

The idea is very simple but extremely powerful.

Instead of upgrading the running application directly, the company runs two environments side by side.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770360856284/cecbd6c4-82f5-46dd-9477-6c9683dc52cc.png align="center")

The Blue environment represents the current live application that users are using.

The Green environment represents the new version of the application. It is fully deployed, fully tested, and fully ready — but hidden from users.

Only one environment receives traffic at a time.

When the company is confident that the Green version is stable, traffic is switched from Blue to Green in one clean step.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770361170074/7ddf5f40-7e2f-4dfb-8c6e-349efb1da5af.png align="center")

No gradual replacement. No mixed versions. No confusion.

If something goes wrong, traffic can be switched back to Blue immediately.

**This is why companies love Blue-Green deployment.**

In real companies, this traffic switch is usually **done using a Kubernetes Service** or **an Ingress controller**. The Service selector is updated to point to the new version. The Pods themselves are not restarted or modified during the switch. Only traffic routing changes.

This makes rollback extremely fast and safe.

For this practical, we have to create two deployments and one service.

So in this scenario, the service will serve the public client requests to that deployment that has matching labels with service labels.

```yaml
vim blue-green-deployment.yml
```

```yaml
# -------------------------------
# BLUE DEPLOYMENT
# -------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: blue-deploy
spec:
  replicas: 4
  selector:
    matchLabels:
      env: blue
  template:
    metadata:
      labels:
        env: blue
    spec:
      containers:
      - name: app
        image: nginx:1.25
        ports:
        - containerPort: 80

---
# -------------------------------
# BLUE SERVICE
# -------------------------------
apiVersion: v1
kind: Service
metadata:
  name: strategy-svc
spec:
  selector:
    env: blue
  ports:
  - port: 80
    targetPort: 80
  type: ClusterIP

## This service will pick blue deployment pods,  because of selector env: blue
---
# -------------------------------
# GREEN DEPLOYMENT
# -------------------------------
apiVersion: apps/v1
kind: Deployment
metadata:
  name: green-deploy
spec:
  replicas: 4
  selector:
    matchLabels:
      env: green
  template:
    metadata:
      labels:
        env: green
    spec:
      containers:
      - name: app
        image: nginx:1.25
        ports:
        - containerPort: 80
```

```yaml
kubectl create -f blue-green-deployment.yml -n strategy
```

```yaml
kubectl get pods  --show-labels -n strategy
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770362100639/b0f9b8df-8997-4b48-8ff4-a1d13edf4d8b.png align="center")

Two deployments are ready, but serving the public request by only one at a time, which has matching service labels.

```yaml
kubectl get svc -n strategy
kubectl describe svc/strategy-svc -n strategy
```

Deployment `blue-deploy` has labels = `env: blue`

Deployment `green-deploy` has labels = `env: blue`

Current Service `strategy-svc` has labels = `env: blue`

Which means deployment `blue-deploy` is currently serving the service, because its pod has matching labels with the service.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770362364062/9737d3a6-6716-470b-86bb-d5e7b44d34b4.png align="center")

Recently company has changed their mind and wants to move on new version. So only a patch change will divert the service request to the new deployment.

```yaml
kubectl patch service strategy-svc \
  -p '{"spec":{"selector":{"env":"green"}}}' -n strategy
```

This patch has changed the traffic from `env: blue` deployment pods

to newer deployment pods `env: green`

Check with the service description. Look into the labels. Now it’s changed to `env:green`.

```yaml
kubectl describe svc/strategy-svc -n strategy
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770362767659/411df339-dd7f-4126-9f59-627804e92bc9.png align="center")

Although In the background, both deployment is running, but deployment that has labels `env: blue` is now serving the service to public.

If company decide to go back with previous version. company need to change only service labels.

```yaml
 kubectl patch service strategy-svc \
  -p '{"spec":{"selector":{"env":"blue"}}}' -n strategy
```

However, Blue-Green is not magic. It does not fix bad database design or incompatible APIs. Companies still need backwards-compatible database migrations and well-designed APIs. Blue-Green simply ensures **that users are never exposed to two application versions at the same time.**

---

Now come to Canary deployment strategy and see what special in this.

4. ## Canary Deployment Strategy
    

Let us first come back to the real-world problem.

A company is running an application that users are actively using. Everything is stable. Payments are working, logins are fine, APIs are responding, dashboards look green. Now the company wants to release a **new version**.

At this point, the company already knows about RollingUpdate and Blue-Green.

RollingUpdate is good, but it allows **mixed versions** to serve traffic at the same time.

Blue-Green is safer, but it switches **100% of users** to the new version at once.

**Now imagine this situation.**

The company is not fully confident about the new version. So

* A new feature is introduced
    
* A new UI flow is added
    
* A new algorithm is used
    
* A performance optimization is done
    

The code has passed testing, but **still the team is not comfortable** exposing **all users** to it **at once**.

So the real question becomes:

“What if we expose the new version to **only a small set of users**, observe it in production, and then decide?”

That thinking is the birth of **Canary Deployment**.

---

**The term *Canary* comes from an old practice in coal mines.**

Miners used to carry a canary bird with them. If the air was toxic, the canary would show signs first, warning the miners before humans were affected.

![Canary Deployment strategy](https://cdn.hashnode.com/res/hashnode/image/upload/v1770623902550/72e6c726-40bc-4ea4-8690-bc7296c2eaac.png align="center")

In software terms, the new version of the application is the **canary**.

It is exposed to danger first, while the majority of users stay safe on the stable version.

---

Now let us define Canary deployment in very simple, honest language.

Canary deployment means:

Releasing a new version of the application to **a small percentage of users**, monitoring its behaviour in real production conditions, and gradually increasing traffic only if everything looks healthy.

**Unlike Blue-Green, Canary is not about instant switching.**

**Unlike RollingUpdate, Canary is not about replacing Pods.**

Canary is about **risk control**.

---

Now it is very important to understand one thing clearly.

Just like RollingUpdate, Canary is **not a default Kubernetes deployment strategy**.

Kubernetes does not have a `type: Canary` field.

Canary is a **deployment pattern** built using Kubernetes primitives such as:

* Deployments
    
* Labels
    
* Services
    
* Ingress or traffic controllers
    

Kubernetes gives you the tools. Canary gives you the idea. Canary deployment is usually done gradually.

First, only a very small percentage of traffic goes to the new version.

So engineers observe the application and environment calmly:

* Checking the Error rates
    
* Checking the Latency
    
* Check the service Logs
    
* Read User complaints
    

If everything looks good, traffic is increased slowly.

If anything looks wrong, Canary is stopped immediately, and users continue using the stable version.

This gives teams **confidence with control**.

---

It is also important to understand that Canary deployment is **more complex** than RollingUpdate and Blue-Green.

It requires or we can say depended on:

* Better monitoring
    
* Clear rollback strategy
    
* Discipline in release management
    

That is why small teams may avoid Canary initially, while mature teams adopt it as they scale.

Companies choose Canary when they feel in control and confident in the application.If you truly understand Canary deployment at this theoretical level, you are already thinking like a production engineer, not just a Kubernetes learner.

---

## Now it’s time for Canary Deployment practical learning.

The company is running a website application named “chatbot“, for this, there is a deployment is running in the production with this specification yaml.

```yaml
vim pre-deployment.yml
```

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: pre-deployment
  labels:
    app: nginx
spec:
  replicas: 4
  selector:
    matchLabels:
      env: prod
      version: v1
  template:
    metadata:
      labels:
        env: prod
        version: v1
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
        ports:
        - containerPort: 80
  
```

In the deployment we have 4 replicas and using nginx image.

labels you can see :

env: prod

version: v1

Now application deployment is exposed using the service (ex: nodePort in our practice).

100% service request came to deployment that has both matching labels.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: pre-svc
spec:
  type: NodePort
  selector:
    env: prod
    version: v1
  ports:
  - port: 80
    targetPort: 80
    nodePort: 31745
```

Now as a client request to application using service request.

```yaml
curl http://node-public-ip:31745
```

You will receive a response from the 4 replica deployment of nginx pods.

```yaml
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
    body {
        width: 35em;
        margin: 0 auto;
        font-family: Tahoma, Verdana, Arial, sans-serif;
    }
</style>
</head>
<body>
<h1>Welcome to nginx!</h1>
<p>If you see this page, the nginx web server is successfully installed and
working. Further configuration is required.</p>

<p>For online documentation and support please refer to
<a href="http://nginx.org/">nginx.org</a>.<br/>
Commercial support is available at
<a href="http://nginx.com/">nginx.com</a>.</p>

<p><em>Thank you for using nginx.</em></p>
</body>
</html>
```

Image explained

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770628147106/1c66db84-5afe-4870-8089-f72d8ba350f8.png align="center")

Now Canary comes in game

Create one more deployment yaml.

```yaml
vim canary-deployment.yml
```

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: canary-deployment
  labels:
    app: httpd
spec:
  replicas: 2
  selector:
    matchLabels:
      env: prod
      version: v2
  template:
    metadata:
      labels:
        env: prod
        version: v2
    spec:
      containers:
      - name: httpd
        image: httpd
        ports:
        - containerPort: 80
  
```

```yaml
kubectl create -f canary-deployment.yml
```

This is new deployment that has 2 replicas and two labels `env: prod` & `version: v2` and using image httpd.

Now we will see the magic of canary strategy.

Instead of fully traffic conversion, we provide a small amount of service.

for this edit the existing service and remove one label `version: v2`

```yaml
kubectl edit svc/pre-svc 
```

```yaml
  ports:
  - nodePort: 31745
    port: 80
    protocol: TCP
    targetPort: 80
  selector:
    env: prod
```

So this time service is controlling and sending client requests to those deployment pods that has labels

env: prod.

and we know both deployment has label `env: prod`.

One deployment `pre-deployment` has 4 replicas

New deployment `canary-deployment` has 2 replicas.

So total there are 6 pods replicas, which in total request client requests via service.

```yaml
kubectl get deployment --show-labels
NAME                  READY   UP-TO-DATE   AVAILABLE   AGE   LABELS
canary-deployment     4/4     4            4           53m   app=nginx,name=canary-deployment
strategy-deployment   2/2     2            2           46m   app=httpd,name=strategy-deployment
```

```yaml
kubectl get pods --show-labels 
NAME                                   READY   STATUS    RESTARTS   AGE   LABELS
canary-deployment-688c4f4d54-ftdt8     1/1     Running   0          53m   env=prod,pod-template-hash=688c4f4d54,version=v1
canary-deployment-688c4f4d54-lzfnz     1/1     Running   0          53m   env=prod,pod-template-hash=688c4f4d54,version=v1
canary-deployment-688c4f4d54-rz4dh     1/1     Running   0          53m   env=prod,pod-template-hash=688c4f4d54,version=v1
canary-deployment-688c4f4d54-zsgjn     1/1     Running   0          53m   env=prod,pod-template-hash=688c4f4d54,version=v1
strategy-deployment-5474844f99-66dc5   1/1     Running   0          46m   env=prod,pod-template-hash=5474844f99,version=v2
strategy-deployment-5474844f99-qhsb6   1/1     Running   0          46m   env=prod,pod-template-hash=5474844f99,version=v2
```

```yaml
curl http://cluster-pub-ip:31745
```

Make it refresh again and again.  
some time nginx image respond and some time httpd image

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770631875946/d9cb4175-a5c1-4dba-ae2e-bb69f3a5c09c.png align="center")

Refresh two three times, because nginx image deployment (older version deployment) has more replicas=4 as compare to newer version deployment replicas=2.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770631809167/1da42375-ef1d-4359-9076-459db24e0a11.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1770631338219/e621f6ab-6ea2-4ade-8019-a9a37fa32644.png align="center")

which mean clients are using newer version of application at the same time but for asmall percentage.

if company found application newer version good, then they can increase the deployment replicas, so percentage share will increase for client requests. and later we can remove the older version deployment pods.

.  
  
Thank you

~Rakesh Kumar Jangid

---

So, how was your experience with this blog post? If you want to read more about Kubernetes and DevOps, we have awesome posts and projects on this website.

Practice Kubernetes GitOps project: [https://projectwala.site/real-world-production-ready-gitops-project-for-devops-practitioners](https://projectwala.site/real-world-production-ready-gitops-project-for-devops-practitioners)

Read other Kubernetes blogs: [Kubernetes-Series](https://projectwala.site/series/kubernetes)

Read Linux blogs: [https://projectwala.site/series/linux-series](https://projectwala.site/series/linux-series)

Read Ansible blogs: [Ansible-Series](https://projectwala.site/series/ansible-playbook)

Learn from DevOps Practice: [DevOps](https://projectwala.site/series/devops)

Read Docker Container: [Docker-Series](https://projectwala.site/series/docker)