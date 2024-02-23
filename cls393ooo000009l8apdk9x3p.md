---
title: "Easy Guide to Prometheus: Installation and Configuration"
datePublished: Thu Feb 01 2024 13:27:18 GMT+0000 (Coordinated Universal Time)
cuid: cls393ooo000009l8apdk9x3p
slug: easy-guide-to-prometheus-installation-and-configuration
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1706793632792/0daedf36-88d2-4c34-9500-32f84df5ee15.jpeg
tags: linux, server, kubernetes, monitoring, devops, dashboard, prometheus, grafana, devops-articles, devops-journey, dashboard-data-analytics, monitoring-tool, devopscommunity, grafana-monitoring, rakamodify

---

---

# **Step 1 (Pre-Setup requirements)**

### **Before You Begin:**

1. Make sure you have the `‘sudo’` access on your Linux server. You’ll need it because this guide uses commands that need `Administrative` permissions.
    
2. Your server needs to be able to connect to the internet. This is necessary to download the Prometheus software. So ping `8.8.8.8` to check connectivity.
    
3. Don’t forget to adjust your firewall settings. You need to allow access to port `9090` on your server to use Prometheus.
    
4. Yum client repository should be configured properly.
    

---

# **Step 2 (Setup Prometheus)**

`Step 2.1:` Update the yum package repositories.

```plaintext
$ sudo yum update -y
```

`Step 2.2:` Go to the official Prometheus downloads page and get the latest [download link](https://prometheus.io/download/) for the Linux binary.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706788133890/390ff68c-887c-4824-bdfd-5553a4c104d8.png align="center")

`Step 2.3:` Retrieve the source code using wget, decompress the tar file, and rename the resulting directory to ‘`prometheus-files’`. For this create a new directory ‘prometheus-files’

```plaintext
$ sudo  wget https://github.com/prometheus/prometheus/releases/download/v2.49.1/prometheus-2.49.1.linux-amd64.tar.gz
$ sudo tar -xvf prometheus-2.49.1.linux-amd64.tar.gz
$ sudo mkdir prometheus-files
$ sudo mv prometheus-2.49.1.linux-amd64  prometheus-files/
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706791597554/e4850ce4-af0d-428f-95af-eab1daa5c95f.png align="center")

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">You can use the MobaXterm remote access tool for Windows. Try this <a target="_blank" rel="noopener noreferrer nofollow" href="https://mobaxterm.mobatek.net/download.html" style="pointer-events: none">LInk</a></div>
</div>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706788846274/6bd2db8a-1fc9-4edf-902a-ef74fbeaed78.png align="center")

---

# **Step 3 (User Creation And Ownership Change)**

`Step 3.1:` Create a Prometheus user, establish the necessary directories, and assign ownership of these directories to the Prometheus user.

```bash
$ sudo useradd prometheus --no-create-home -s /bin/false 
$ sudo mkdir /etc/prometheus
$ sudo mkdir /var/lib/prometheus
$ sudo chown prometheus:prometheus /etc/prometheus
$ sudo chown prometheus:prometheus /var/lib/prometheus
```

`Step 3.2:` Take the ‘prometheus’ and ‘`promtool’` files from the ‘prometheus-files’ folder. Put them in the ‘/usr/local/bin’ folder. Then, make sure they belong to the ‘prometheus’ user. so change the ownership to prometheus user

```plaintext
$ sudo cp prometheus-files/prometheus /usr/local/bin/
$ sudo cp prometheus-files/promtool /usr/local/bin/
$ sudo chown prometheus:prometheus /usr/local/bin/prometheus
$ sudo chown prometheus:prometheus /usr/local/bin/promtool
```

`Step 3.3:` Move the consoles and console\_libraries directories from prometheus-files to /etc/prometheus folder and change the ownership to prometheus user.

```plaintext
$ sudo cp -r prometheus-files/consoles /etc/prometheus
$ sudo cp -r prometheus-files/console_libraries /etc/prometheus
$ sudo chown -R prometheus:prometheus /etc/prometheus/consoles
$ sudo chown -R prometheus:prometheus /etc/prometheus/console_libraries
```

---

# Step 4 (Prometheus Configuration Process)

All the prometheus configurations should be present in `/etc/prometheus/ prometheus.yml file.`

`Step 4.1:` Create the prometheus.yml file & Copy the following contents to the prometheus.yml file.

```plaintext
$ sudo vi /etc/prometheus/prometheus.yml
```

```plaintext
global:
  scrape_interval: 10s

scrape_configs:
  - job_name: 'prometheus'
    scrape_interval: 5s
    static_configs:
      - targets: ['localhost:9090']
```

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><mark>NOTE: Make sure you have added </mark><code>9090</code><mark> port in firewall.</mark></div>
</div>

```plaintext
$ sudo firewall-cmd --permanent-port=9090/tcp
$ sudo firewall-cmd --reload
$ sudo firewall-cmd --list-all
```

`Step 4.2:` Change the ownership of the file to prometheus user.

```plaintext
$ sudo chown prometheus:prometheus /etc/prometheus/prometheus.yml
```

`Step 4.3:` Create a prometheus service file & Copy the following content to the file, for Setup Prometheus Service File.

```plaintext
$ sudo vi /etc/systemd/system/prometheus.service
```

```plaintext
[Unit]
Description=Prometheus
Wants=network-online.target
After=network-online.target

[Service]
User=prometheus
Group=prometheus
Type=simple
ExecStart=/usr/local/bin/prometheus \
    --config.file /etc/prometheus/prometheus.yml \
    --storage.tsdb.path /var/lib/prometheus/ \
    --web.console.templates=/etc/prometheus/consoles \
    --web.console.libraries=/etc/prometheus/console_libraries

[Install]
WantedBy=multi-user.target
```

`Step 4.4:` Reload the systemd service to register the prometheus service and start the prometheus service.

```plaintext
$ sudo systemctl daemon-reload
$ sudo systemctl start prometheus
```

Check the prometheus service status using the following command.

```plaintext
$ sudo systemctl status prometheus
```

The status should show the active state as shown below.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706791534981/9473b486-6e8e-4c37-91ea-a510bfefcb0f.png align="center")

---

# **Step 5 (Access Prometheus Web UI)**

Now you will be able to access the prometheus UI on `9090` port of the prometheus server.

```plaintext
http://<Instance-IP>:9090/graph
```

You can see the following UI as shown below. Lots of Congratulations !!!!

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706790680007/34e467df-a9e9-4e43-807e-9cb724ac22be.png align="center")

Now search `"process_cpu_seconds_total"` in search bar, choose option Graph and press `Execute` .

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706792331299/5e581ee8-0e5f-456c-9404-238dac0fe5b1.png align="center")

This is graphical representation for `"process_cpu_seconds_total"` of your instance.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1706792344905/b8938720-f5fc-426b-ac5f-e5d3ea77b029.png align="center")

# Step 6 (What Next.....?)

`Step 6.1:` Well At this point, we’ve set up the Prometheus server. But to start collecting data, we need to specify where to get it from. This is done by registering a ‘target’ in the `prometheus.yml` file.

1. A ‘target’ is essentially a source system from which Prometheus can collect metrics. If you have multiple systems (like ten servers) that you want to monitor, you would list the IP addresses of these servers as targets in the Prometheus configuration.
    
2. However, before Prometheus can collect any data, each server needs to have a program called ‘Node Exporter’ installed. This program collects system metrics and makes them available for Prometheus to scrape.
    

In simpler terms, think of it like this: Prometheus is a data collector, the ‘targets’ are the places it collects data from, and ‘Node Exporter’ is the tool that gathers the data and puts it in a place where Prometheus can find it.

`Step 6.2:` How to do practically ?

Here are the practical steps to get data from 10 servers using Prometheus and Node Exporter:

1. **Install Node Exporter on Each Server**: Node Exporter is a program that collects system metrics and makes them available for Prometheus to scrape. You need to install Node Exporter on each of the 10 servers that you want to monitor.
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">What is Node Exporter ?</div>
</div>

> Node Exporter is like a reporter for your server. It collects information about your server’s performance, such as how much memory it’s using, how much data it’s reading and writing to the disk, and how much work the CPU is doing. It then makes this information available in a format that Prometheus, a monitoring tool, can understand. This allows you to keep track of your server’s health and performance over time.

1. **Configure Prometheus to Monitor These Servers**: After installing Node Exporter, you need to tell Prometheus to scrape metrics from these servers. This is done by adding the IP addresses of these servers as targets in the `prometheus.yml` configuration file.
    

Here’s an example of what the configuration might look like:

```plaintext
$ sudo vim /etc/prometheus/prometheus.yml
```

```yaml
scrape_configs:
  - job_name: 'node'
    static_configs:
      - targets: ['<server-1-ip>:9100', '<server-2-ip>:9100', ..., '<server-10-ip>:9100']
```

Replace `<server-1-ip>`, `<server-2-ip>`, …, `<server-10-ip>` with the actual IP addresses of your servers.

1. **Start Prometheus**: Finally, start the Prometheus server. It will now begin collecting metrics from the specified targets at regular intervals.
    

---

References:

* [https://prometheus.io/docs/visualization/grafana/](https://prometheus.io/docs/visualization/grafana/)
    
* [https://mobaxterm.mobatek.net/download.html](https://mobaxterm.mobatek.net/download.html)