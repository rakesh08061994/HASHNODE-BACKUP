---
title: "How to setup Kubernetes cluster over cloud on Ubuntu OS"
datePublished: Tue Nov 07 2023 11:06:41 GMT+0000 (Coordinated Universal Time)
cuid: cloo87lon001308jkgunb4iy1
slug: how-to-setup-kubernetes-cluster-over-cloud-on-ubuntu-os
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1699355073221/ce61d21d-c9dc-49af-812b-465be2e3f979.png
tags: ubuntu, deployment, kubernetes, containers, cluster

---

Embarking on your Kubernetes cloud cluster journey for practice may seem daunting, but fear not. We're here to walk you through the process, step by step, as you set up a Kubernetes cluster on the Ubuntu OS in the cloud.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Pre-configuration for cluster nodes (Step-1 to Step-6) on each node instance</div>
</div>

### Create instances over the cloud

I am taking here AWS instances t2.medium, ubuntu OS, 20 GB storage each, Firewall security Allows ALL traffic, and swap memory disabled. I will go with three nodes cluster (1 Master + 2 Worker Node) with the same above configuration.

| Instance Type | Configuration | Storage |
| --- | --- | --- |
| T2.medium or higher | 2vC Core + 4 GB RAM or more | 20 GB or more |

---

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">To get remotely access of cluster nodes on windows OS, you can download this "MobaXterm" application from this link : <a target="_blank" rel="noopener noreferrer nofollow" href="https://mobaxterm.mobatek.net/download.html" style="pointer-events: none">https://mobaxterm.mobatek.net/download.html</a></div>
</div>

### Step - 1 (Create a non-root user and allow sudoers privileges)

We are going to create a new user admin (If there is not) and assign sudoers privileges to him. so for this we create a new folder under /etc/sudoers.d/admin, and do the below entry in /etc/sudoers.d/admin. Dont forget to restart sshd service

```bash
$ sudo adduser admin
$ sudo echo "admin    ALL=(ALL)   NOPASSWD:ALL" >> /etc/sudoers.d/admin
$ sudo systemctl restart sshd
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">NOTE: We'll execute each command using an admin user, not the root user, for enhanced security and best practices</div>
</div>

---

### Step - 2 ( Define your machine Hostname )

Change the Hostname of each machine using hostnamectll command.

> | Machine (Public\_IP) | Machine (Private\_IP) | Hostname |
> | --- | --- | --- |
> | 52.168.32.71 | 172.25.32.32 | masternode.example.com |
> | 52.168.23.28 | 172.35.32.64 | workernode1.example.com |
> | 52.168.23.28 | 172.25.64.63 | workernode2.example.com |

```bash
$ sudo hostnamectl set-hostname <your-hostname>
$ sudo exec bash    # execute the current shell with latest changes 
$ hostname
```

---

### Step - 3 (Host entry with private IP & hostname)

```bash
$ sudo vi /etc/hosts

172.25.32.32        masternode.example.com
172.35.32.64        workernode1.example.com
172.25.64.63        workernode2.example.com
```

> Note: Ping all machines to each other

---

### Step - 4 ( Allow some entry in sshd\_config file)

In /etc/ssh/sshd\_config file uncomment and allow the following lines.

```bash
$ sudo vi /etc/ssh/sshd_config

PermitRootLogin yes
PubkeyAuthentication yes
PasswordAuthentication yes
```

And restart sshd service

```bash
$ sudo systemctl restart sshd
$ sudo systemctl enable sshd
```

---

### Step - 5 (Create SSH key and copy to worker node instances)

Generate an SSH key and distribute it to your worker node instances for secure and efficient communication. This step involves creating an SSH key and seamlessly deploying it across your worker node instances to streamline the communication process.

```bash
$ ssh-keygen
$ ssh-copyid workernode1.example.com
$ ssh-copyid workernode2.example.com
```

---

### Step-6 (Disable swap memory & Add kernel Parameters)

```bash
$ sudo swapoff -a
$ sudo sed -i '/ swap / s/^\(.*\)$/#\1/g' /etc/fstab
```

---

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">NOTE: All pre-configurations is completed. So let's move to setup Kubernetes setup installation.</div>
</div>

### Step - 7 ( Run the following commands on each instance node as admin user rights )

```bash
$ sudo tee /etc/modules-load.d/containerd.conf <<EOF
overlay
br_netfilter
EOF
$ sudo modprobe overlay
$ sudo modprobe br_netfilter


$ sudo tee /etc/sysctl.d/kubernetes.conf <<EOF
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
net.ipv4.ip_forward = 1
EOF 


$ sudo sysctl --system


$ sudo apt install -y curl gnupg2 software-properties-common apt-transport-https ca-certificates


$ sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmour -o /etc/apt/trusted.gpg.d/docker.gpg
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"


$ sudo apt update
$ sudo apt install -y containerd.io


$ containerd config default | sudo tee /etc/containerd/config.toml >/dev/null 2>&1
$ sudo sed -i 's/SystemdCgroup \= false/SystemdCgroup \= true/g' /etc/containerd/config.toml


$ sudo systemctl restart containerd
$ sudo systemctl enable containerd
```

Add Repository for kubernetes

```plaintext
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.28/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.28/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
```

> Install kubelet, kubectl, kubeadm

```bash
$ sudo apt update
$ sudo apt install -y kubelet kubeadm kubectl
$ sudo apt-mark hold kubelet kubeadm kubectl
```

---

### Step - 8 ( Run "kubeadm init" On Master Node to create clusters master node)

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Initialize Kubernetes cluster with kubeadm (Only on master node).</div>
</div>

```bash
$ sudo kubeadm init --control-plane-endpoint=<your-master-node-hostname>
```

> NOTE: on master node with the admin user. and check status of master node

```bash
$ mkdir -p $HOME/.kube
$ sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
$ sudo chown $(id -u):$(id -g) $HOME/.kube/config

# To check either cluster is setup being proper setup or not, and how many nodes are connected yet.
# Also check that kubernetes resources is proper installed or not.

$ kubectl get nodes -o wide
$ kubectl get pods -n kube-system
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Install CNI plugin CALICO on master node as admin user rights.</div>
</div>

```bash
$ kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.25.0/manifests/calico.yaml
```

---

### Step - 9 (Run "kubeadm join" on worker nodes To join with master node in the cluster)

```bash
$ sudo kubeadm join masternode.example.net:6443 --token vt3ua6.scma2y8rl4menfh2 \
   --discovery-token-ca-cert-hash sha256:049xaa7fcdced8a8e7b20d37ec0c5dd699ds5f8x616885697q2ff917d4c94962a36
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">NOTE: Your setup is being created. Congratulation !</div>
</div>

---

### Step - 10 (Test your kubernetes cluster to Deploy an application)

```bash
$ kubectl create -f https://raw.githubusercontent.com/kubernetes/website/main/content/en/examples/controllers/nginx-deployment.yaml
```

```bash
$ kubectl expose deployment nginx-deployment --name=my-svc --port=80 --target-port=80 --type=NodePort
$ kubectl get svc

NAME       TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)        AGE
my-svc     NodePort   10.100.124.129   <none>        80:32567/TCP   2m
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Check your nginx web application publically, for this find your any instances nodes public IP address and then colon 32567. For example go to web broswer like chrome or firefox</div>
</div>

```bash
<Public-IP-of-any-of-nodes>:32567
```

### Congratulations........It works! Thank you!

---

### References:

* Deployment documentation:- [https://kubernetes.io/docs/concepts/workloads/controllers/deployment/](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
    
* Download MobaXterm for your windows machine to get ssh over cloud instances:- [https://mobaxterm.mobatek.net/download.html](https://mobaxterm.mobatek.net/download.html)