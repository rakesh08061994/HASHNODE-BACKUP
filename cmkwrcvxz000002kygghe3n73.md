---
title: "Real-World, Production-Ready GitOps Project for DevOps Practitioners"
datePublished: Tue Jan 27 2026 15:35:25 GMT+0000 (Coordinated Universal Time)
cuid: cmkwrcvxz000002kygghe3n73
slug: real-world-production-ready-gitops-project-for-devops-practitioners

---

Hello, this is **Rakesh Kumar** — your DevOps project practice trainer and your friend.  
I’m back again with a **brilliant DevOps project** that is not only **production-ready** but also **highly valuable for real-world learning**.

This project is designed to take you **deep inside the core of DevOps practices**. We will not just run commands — we will understand **why things work the way they do in real production environments**.  
By the end of this project, you won’t be the same person. You’ll gain **real-world, production-level insights** that most beginners miss.

---

## Tech Stack Used

In this project, we will work with the following tools and technologies:

* **Linux**
    
* **LAMP Server (WordPress)**
    
* **Docker + Kind** (to create a mini Kubernetes practice cluster)
    
* **Kubernetes** (for microservices-based application deployment)
    
* **Kubernetes Dashboard** (for pod-level monitoring)
    
* **ArgoCD** (GitOps tool to tightly sync Git & GitHub for continuous deployment)
    
* **Helm** (your special package manager for Kubernetes)
    
* **AWS EC2 (for Project Infra, t2.large instance)**
    
* **Git & GitHub**
    

---

## Core Skills You Should Have

Before starting this project, you should be comfortable with:

* Basic **Linux** commands
    
* **Git & GitHub** (basic usage)
    
* **Docker and Kubernetes** fundamentals
    
* **AWS EC2 instance** creation
    
* Basic **Linux web server** knowledge
    

Don’t worry — you don’t need to be an expert.  
If your basics are clear, this project will **sharpen your mindset and confidence**.

---

### Let’s Get Started

I am using aws cloud for project infrastructure. So we will use  
OS: Ubuntu 22.04  
Configuration: T2.Large (Because we have to do lots of work here- so need more power)  
Storage Volume: 24 GB Minimum

## **Step-1: Create AWS T2.Large Instance**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769517801215/905f659e-24b1-4d06-83c0-fdef761f99d2.png align="center")

  
We will use direct aws console to access terminal

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769517869175/97cb1a4f-adac-4f31-a579-afe635158395.png align="center")

Install some required packages tool tech

```plaintext
apt-get update
apt install -y vim git docker.io 
systemctl enable --now docker
```

Step-3: Now we have to install KIND so we can create k8s mini cluster. So for this we have to create some script. and then run the script after give the execute permission.

```plaintext
# vim install_kind.sh

#!/bin/bash
# For AMD64 / x86_64
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.20.0/kind-linux-amd64
chmod +x ./kind
sudo cp ./kind /usr/local/bin/kind
rm -rf kind 
```

```plaintext
chmod +x install_kind.sh
bash install_kind.sh
```

In Ubuntu Install Docker

```plaintext
apt-get update
apt install docker.io
systemctl enable --now docker
systemctl status docker
docker ps -a
```

In Fedora Based System Install Docker

```plaintext
sudo dnf remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

```plaintext
sudo dnf -y install dnf-plugins-core
sudo dnf config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

```plaintext
sudo dnf install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

```plaintext
sudo systemctl enable --now docker
sudo docker ps -a
```

Your Docker is installed successfully. However, to access the Kubernetes cluster, you need a command-line tool, which is "kubectl."

## **Step-3: Install kubectl command in KIND cluster.**

```plaintext
# vim install_kubectl.sh
#!/bin/bash

# Variables
VERSION="v1.30.0"
URL="https://dl.k8s.io/release/${VERSION}/bin/linux/amd64/kubectl"
INSTALL_DIR="/usr/local/bin"

# Download and install kubectl
curl -LO "$URL"
chmod +x kubectl
sudo mv kubectl $INSTALL_DIR/
kubectl version --client

# Clean up
rm -f kubectl

echo "kubectl installation complete."
```

```plaintext
chmod +x install_kubectl.sh
bash install_kubectl.sh
```

## **Step-4: Install the KIND cluster,** so we have to create a KIND config file, that specify the core specification details regarding your KIND cluster nodes.

```plaintext
# vim config.yml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4

nodes:
- role: control-plane
  image: kindest/node:v1.30.0
- role: worker
  image: kindest/node:v1.30.0
- role: worker
  image: kindest/node:v1.30.0
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">This project will use KIND version 1.30. because till today this is latest and stable KIND version for production application deployment.</div>
</div>

Create the KIND cluster with specifying config.yml file for reference

```plaintext
kind create cluster --config=config.yml
```

and you will get screen like this.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769519180355/3b6fa285-d881-45b6-bd5a-3101d3705bea.png align="center")

Your KIND kubernetes cluster is working or not, let him check

```plaintext
kubectl get no -o wide
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769519350514/68e5f494-ed2f-49b0-86b0-c92100604326.png align="center")

## **Step-5: The GitHUB Repository Server**

Over this KIND cluster, your application will deploy. But what about the project application files? As you know, we are working on a LAMP WordPress application, and we have a dedicated GitHub repository server for this, where you will get all the required files and folders. Because this is a GitOps project, GitHub is the core artifact server.

Go to this link: [devrakaops/projectwala](https://github.com/devrakaops/projectwala)

This is the huge repository where some of my core learning DevOps project are kept, this project is one of them.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769519846192/4e27d099-edc5-414e-801f-026aba32002c.png align="center")

In this repository the related files and folder for this project are kept here only.

Go to this link: [projectwala/Basic-Level/Project-2 at main · devrakaops/projectwala](https://github.com/devrakaops/projectwala/tree/main/Basic-Level/Project-2)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769519936430/9f03b4b6-f9f9-4b71-83fb-7a51b802dc61.png align="center")

The Kubernetes folder has all the YAML for our project, which we will use.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769520011702/6d1cde76-031f-422a-9c2d-dc2ec7797efc.png align="center")

## **Step-6. Installing Argo CD**

We have multiple options to install ArgoCD

1. **Using Helm install ArgoCD**
    
    To install ArgoCD using helm, you have to first install helm package manager in your kubernetes cluster itself and after then need to install using dedicated yaml file. I am here providing you a link:
    
2. **Using Direct command install ArgoCD**
    
    To install argocd using direct command line method follow the commands
    
    Create a namespace for Argo CD:
    
    ```plaintext
    kubectl create namespace argocd
    ```
    
    Apply the Argo CD manifest:
    
    ```plaintext
    kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
    ```
    
    Check services in Argo CD namespace:
    
    ```plaintext
    kubectl get svc -n argocd
    ```
    
    Expose Argo CD server using NodePort:
    
    ```plaintext
    kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort"}}'
    ```
    
    Forward ports to access Argo CD server:
    
    ```plaintext
    kubectl port-forward -n argocd service/argocd-server 443:443 &
    ```
    

Access the ArgoCD cluster using public IP of your AWS instance with dedicated 443 port. This is not fix that only use 443 port. You can use any random port, because we are using port forward so request will come at the end of the service port

* Don’t forgot to open 443 ports in your AWS security group inbound rule
    

In starting you will see the unsecure page warning

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769521174651/392f30fa-be55-40f1-be33-3bc46b0c2a56.png align="center")

But click on “Continue to 13.201.28.87 (unsafe)“ link. And you will get the actual ArgoCD UI Page.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769521255427/5dffbbb6-5104-43ee-9608-6969efc88fbb.png align="center")

You can cross-check in Kubernetes cluster as well.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769523657069/e35ee2a3-5d4c-4d2d-aba2-5fce106558d4.png align="center")

Now it’s time to access the ArgoCD, you required username and password:

The username is "admin," but the password can only be obtained by decoding a secret using the base64 algorithm.

Run this command to Retrieve Argo CD admin password:

```plaintext
kubectl get secret -n argocd argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d && echo
```

```plaintext
jr20RBeyfzwvB1mW
```

Paste the password to the UI dashboard  
**Username:** admin  
**Password:** jr20RBeyfzwvB1mW

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769521615107/dbd74630-72f3-4591-b55e-4e2baca8bd75.png align="center")

This is simple interface of ArgoCD dashboard.

## **Step-7: Setup the application in ArgoCD**

Click on `+New APP` Icon and click on `EDIT AS YAML` icon, just left top side, so paste the code below

```plaintext
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: myapp
spec:
  destination:
    namespace: default
    server: https://kubernetes.default.svc
  source:
    path: Basic-Level/Project-2/Kubernetes
    repoURL: https://github.com/devrakaops/projectwala.git
    targetRevision: main
  sources: []
  project: default
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
      enabled: true
```

Save this and click on `CREATE` .

Your application is running, and within 5 seconds, it will sync with your GitHub application directory YAML in the Kubernetes folder.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769522590789/34ab07c8-d1ea-418d-bf5a-a42fc16a7602.png align="center")

Just click on this.  
And you will see the magic of GitOps.

All kubernetes YAML is showing in tree wise structure. all are healthy and working properly.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769522644937/a0c1d912-35c2-482a-84de-25fedf97cc00.png align="center")

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">If you want to know the resource specifications, just click on GUI icon of that resource.</div>
</div>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769522822668/b29496e8-5e8f-484e-af00-bdced5c0a329.png align="center")

Either make changes on GitHub repository folder or direct change here will impact the resource.

If you will check at the kubernetes cluster using

```plaintext
kubectl get all -n default
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769522971441/63c64738-1ee9-434e-96bc-8c97285eee03.png align="center")

Which means ArgoCD is working properly.

Now its time to expose the WordPress deployment using port forwarding.

```plaintext
kubectl port-forward  svc/wordpress -p 8080:80 --address=0.0.0.0 &
```

I have used 8080 for mapping, that is mapped inside with port 80 and accessable from everywhere.

Now you can access your wordpress application on port 8080 specify with your public IP of AWS instance. As i told you earlier that this is not fix that only expose application on 8080. You can use any random open port that is not using currently, means shold be free. so don’t forgot to open 8080 port in AWS instances securit groups inbound rule.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769523404927/db3acd8f-b063-4781-8640-d57930f51417.png align="center")

Fill the WordPress details.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769523460513/b876564b-aedc-4660-8b14-efcc4f540aa4.png align="center")

And now take login with login credentials.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769523509115/0a612eb3-95fe-4518-bc54-37df9bf29a12.png align="center")

Setup for LAMP WordPress theme or customize your application.

Finally you will get the application at the end.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769523725304/caee6e68-12bc-478a-ad1c-b7e363831431.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769523787712/b88fed7a-5e3e-45e5-9f0e-767c77d39da3.png align="center")

## **Step-8: Install Kubernetes Dashboard for pod level monitoring**

* Deploy Kubernetes dashboard:
    
    ```plaintext
    kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
    ```
    
* Create a token for dashboard access:
    
    ```plaintext
    kubectl -n kubernetes-dashboard create token admin-user
    ```
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">You will get this error that you don’t have role “admin-user“</div>
</div>

So create a service role “admin-user“ and make him binding with service account so we can access the kubernetes-dashboard using the token of service account

```plaintext
# vim dashboard_admin.yml

apiVersion: v1
kind: ServiceAccount
metadata:
  name: admin-user
  namespace: kubernetes-dashboard
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: admin-user
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: cluster-admin
subjects:
- kind: ServiceAccount
  name: admin-user
  namespace: kubernetes-dashboard
```

Make port mapping for kubernetes-dashboard, so you can access the dashboard. So first check the service for the kubernetes-dashboard.

```plaintext
kubectl get svc -n kubernetes-dashboard
```

You will see kubernetes-dashboard service is a Cluster-IP Service that is only accessable on port 443 inside the cluster only, not from outside.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769524481722/c5005a5a-1e94-4fe9-921a-0ae84a79395e.png align="center")

So lets have a port mapping to access the kubernetes-dashboard via the service. so 9090 port is opening here to access kubernetes-dashboard that is mapped with port 443 inside.

```plaintext
kubectl port-forward  svc/kubernetes-dashboard -n kubernetes-dashboard -p 9090:443 --address=0.0.0.0 &
```

Access the dashboard on port 9090

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769524633421/71e28616-76f4-4ba7-814a-8e1ddd20eeac.png align="center")

You can see that the **Kubernetes Dashboard is accessible only when we provide a token**.  
This is because Kubernetes follows a **security-first approach by default**.

Now, let’s understand this in easy language.

Kubernetes Dashboard is nothing but a **pod running inside the Kubernetes cluster**, right?  
But Kubernetes does not allow **any pod or user** to access cluster information by default.

So if we try to open the dashboard **without permission**, Kubernetes will block the access.

That’s why we need to create a **ServiceAccount**.

A **ServiceAccount** tells Kubernetes:

> “This dashboard pod is trusted, and it is allowed to view cluster resources.”

Using this ServiceAccount, Kubernetes generates a **token**.  
When we log in to the dashboard using this token, Kubernetes verifies the permissions and then allows access.

So in this step, we are creating a **Service Account (and assigning proper role)** so the Kubernetes Dashboard can securely access the cluster resources.

```plaintext
kubectl create -f dashboard_admin.yml
```

If you check you will see a service account named “admin-user“

```plaintext
kubectl get sa -n kubernetes-dashboard
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769524303109/c67b9197-cafd-411f-bccd-bda7973d76a1.png align="center")

Now create the token and paste it to token section in dashboard UI.

```plaintext
kubectl -n kubernetes-dashboard create token admin-user
```

You will get something like this

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769525148329/59533900-d7ee-4a2b-9d12-25b93bfa479b.png align="center")

```plaintext
eyJhbGciOiJSUzI1NiIsImtpZCI6Ik8wRnE3NDRTcXVHUHdsMHB3eUw1bmRNX3lwUDZjNWlkYUJ4aThNM01KQkkifQ.eyJhdWQiOlsiaHR0cHM6Ly9rdWJlcm5ldGVzLmRlZmF1bHQuc3ZjLmNsdXN0ZXIubG9jYWwiXSwiZXhwIjoxNzY5NTI4NzE5LCJpYXQiOjE3Njk1MjUxMTksImlzcyI6Imh0dHBzOi8va3ViZXJuZXRlcy5kZWZhdWx0LnN2Yy5jbHVzdGVyLmxvY2FsIiwianRpIjoiNThhYzI5ZDYtZGQxNi00YjA4LTg4ZGYtYTAxM2IyZmNkOWVjIiwia3ViZXJuZXRlcy5pbyI6eyJuYW1lc3BhY2UiOiJrdWJlcm5ldGVzLWRhc2hib2FyZCIsInNlcnZpY2VhY2NvdW50Ijp7Im5hbWUiOiJhZG1pbi11c2VyIiwidWlkIjoiYWE1M2MyYzctNmU4Ni00ZTY3LThkYmItYTI1MmE1ZTAzOTA0In19LCJuYmYiOjE3Njk1MjUxMTksInN1YiI6InN5c3RlbTpzZXJ2aWNlYWNjb3VudDprdWJlcm5ldGVzLWRhc2hib2FyZDphZG1pbi11c2VyIn0.HPJbXiKqjUBXQxYV47F2_kQ1fcgkHitAqRBdqmVQqn4tyDP2zQOAjPuqJWYDKu8t75KjjkmPu8bmOrznuEFJq3d42tyzPa62dSx8CuMpSa_GJ2h9SqwjpYJ46-PtdBy4kczEn4fidvMRLhI1wDYn8ne16if2YZqL--mYpAUR1LG2IEikidTDpFwZY5FkW8Am09SMIESV4u_JfrwxpTgJvB_9l1iXNCNXApujYnBEWEjcc479heqmzwdvQy6pBUq3sn5KgfenzbjhLzJZUI6nwIeKOOS3j_UUcyYsIrDxUwtkbzjQ0VLKZkMmcOVrV41tzdEIcIkRqbX6oLIlV-asQQ
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769525199042/3d431de6-0b7a-4d5a-9c07-673a8359446d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769525228671/eb8eba01-e27c-4bc0-a77d-deda11eaa110.png align="center")

You will get the complete resources namespace vise

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769525282411/4f14b867-8100-4258-97a0-a10884114657.png align="center")

Change the namespace and you can access the related resources of namespace.

  
There are many possibilities in this project:

* We can add monitoring pods for metrics and log-based monitoring using Prometheus, Grafana, Loki, and exporters.
    
* We can set up Kubernetes pod autoscaling and more.
    

## **Step 9: Set up Pod Autoscaler for load-based deployment management**

To setup a Pod AutoScaller, we required official yaml. See the link: [HorizontalPodAutoscaler Walkthrough | Kubernetes](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale-walkthrough/)

Create a HPA YAML and customize it. I have created the complete yaml for you.  
SO simply Copy-Paste and create the resource.

```yaml
---
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: php-apache
spec:
  behavior:
    scaleDown:
     stabilizationWindowSeconds: 300
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: wordpress
  minReplicas: 1
  maxReplicas: 5
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 50
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769526424294/9f6162c6-0e3e-427c-a740-6e37bf86224a.png align="center")

If you see carefully HPA is waiting for matrix, so HPA over it can work.  
If we dont have HPA, this wont work at all. so just check matrix-server is running or not.

```yaml
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```

Just edit one thing

```yaml
kubectl edit deployment metrics-server -n kube-system
```

Add this arg flag “`--kubelet-insecure-tls`“ in “container.args“

```yaml
spec:
      containers:
      - args:
        - --kubelet-insecure-tls
        - --cert-dir=/tmp
        - --secure-port=10250
        - --kubelet-preferred-address-types=InternalIP,ExternalIP,Hostname
        - --kubelet-use-node-status-port
        - --metric-resolution=15s
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769527119975/dcb7aa74-5150-46f1-8611-4009fb819250.png align="center")

Now check again the HPA status

```yaml
kubectl get hpa 
```

```yaml
NAME         REFERENCE              TARGETS       MINPODS   MAXPODS   REPLICAS   AGE
php-apache   Deployment/wordpress   cpu: 0%/50%   1         5         1          6m40s
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1769527940042/e827e617-1926-43af-8a1c-ecb3944676e4.png align="center")