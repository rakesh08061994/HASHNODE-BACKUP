---
title: "Linux Services & Daemons: The Hidden Hero's of your Linux Server"
datePublished: Thu Feb 15 2024 08:57:51 GMT+0000 (Coordinated Universal Time)
cuid: clsmzn3gj000l09ky6oerg3f5
slug: linux-services-daemons-the-hidden-heros-of-your-linux-server
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1707975506523/226c0a54-a330-4693-b340-6866c384d355.png
tags: linux, system-architecture, systemd, linux-for-beginners, linux-basics

---

---

### Introductions & Importance

In a Linux server, services and daemons are like the unsung heroes working behind the scenes to ensure everything runs smoothly. They are essentially programs that run in the background, performing various tasks necessary for the system to function properly.

Here are some examples:

1. `Web Server` **(e.g., Apache or Nginx)**: This service is responsible for serving web pages. When you type a URL into your browser, the request goes to the web server, which then sends back the requested page. Without this service, your website wouldn’t be accessible to users.
    

1. `NTP Server` **(Network Time Protocol)**: This daemon synchronizes the system’s clock with global time servers. Accurate timekeeping is crucial for many server tasks and processes. For example, it helps in scheduling tasks, logging events accurately, and ensuring secure communication.
    

1. `SSH Server:` This service allows secure remote access to the server. Administrators use SSH to log in and manage the server from any location. Without the SSH service, remote management would be much more difficult and less secure.
    

Imagine a busy airport - the services and daemons are like the air traffic control, baggage handling, and maintenance crews. You might not see them, but without them, planes wouldn’t be able to land or take off safely, passengers wouldn’t get their luggage, and the whole operation would come to a standstill.

So, in a nutshell, services and daemons are vital for the continuous and correct operation of a Linux server. They handle essential tasks and enable the server to perform its intended functions seamlessly. So now important question is what is Daemons and Service in Linux.

---

### What is daemon(s)

In Linux, a `daemon` is a background process that operates autonomously, performing tasks without user intervention. They are utility programs that run silently in the background to monitor and take care of certain subsystems to ensure that the operating system runs properly. Almost all daemons have names that end with the letter `“d”`. For example, `httpd` is the daemon that handles the Apache server, and `sshd` handles SSH remote access connections.

Daemons are important in a Linux OS server for several reasons:

1. `Handling Network Requests:` Daemons enable your system to correctly respond to network requests by associating each request with a compatible network port.
    
2. `Executing Scheduled System Tasks:` Daemons make it possible to run or execute scheduled system tasks. The daemon responsible for this specific task is called `cron`.
    
3. `Monitoring System Performance:` Daemons also offer a priceless contribution in monitoring the performance of your system.
    
4. `Managing Essential Services:` They act as the backbone of many essential computing services, operating silently and efficiently. From managing system logs with the `syslogd` daemon to handling mail services with the `postfix` daemon, these background processes are integral to the functionality and efficiency of our systems.
    

Now, let’s understand the difference between `a Process`, `a Daemon`, and `a Service`:

* `A Process` is a running instance of executing program code. At a particular instant of time, it can be either running, sleeping, or zombie (completed process, but waiting for its parent process to pick up the return value).
    
* `A Daemon` is a specific type of process that runs in the background and is not interactive. They have no controlling terminal. They perform certain actions at predefined times or in response to certain events. In Unix-like systems, the names of daemons end in ‘d’.
    
* `A Service` is a program that responds to requests from other programs over some inter-process communication mechanism (usually over a network). `A service doesn’t have to be a daemon, but usually is`. A user application with a GUI could have a service built into it. For example, a file-sharing application. In Windows, daemons are called services. In essence, daemons are the silent heroes of computing, managing tasks and services that ensure our systems run smoothly. They are effectively invisible but essential.
    

---

### What is systemd?

`systemd` is also a daemon. It is a system and service manager for Linux operating systems. It is designed to be backward compatible with SysV init scripts and provides several features such as

* parallel startup of system services at boot time,
    
* on-demand activation of daemons,
    
* dependency-based service control logic.
    

Its primary component is a `“system and service manager”` – an init system used to bootstrap user space and manage user processes. It also provides replacements for various daemons and utilities, including device management, login management, network connection management, and event logging.

```sql
# pstree | less
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707895128938/ea6049ea-9819-4e9e-9992-d7df5620b06a.png align="center")

---

### What are Service Units?

In RHEL Linux, systemd uses something called “units” to manage different types of tasks. Here are the three types of units mentioned:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1707982696103/88e7ce11-61cd-4f95-9ae0-476062777119.png align="center")

1. **Service Units (.service)**: Service units have a `.service` extension and represent system services. You can use service units to start frequently accessed daemons, such as a web server.
    
2. **Socket Units (.socket)**: These are like the telephone operators of your system. They monitor communication points (sockets) between different processes. If a process wants to talk to another (connects to the socket), systemd starts the service (like a worker) needed for that communication.
    
3. **Path Units (.path)**: These are like the watchmen of your system. They keep an eye on specific locations in your filesystem. If they notice a change (like a new file being added), they can start a service.
    
4. Daemons (.d): daemons are indeed a part of system units. In the context of systemd, a daemon is often associated with a **service unit**. When a service unit is started, it usually initiates a daemon. A daemon is a type of program that runs in the background, waiting for events to occur and offering services. A good example is a web server daemon, which waits for a request to come in, and then responds to that request.
    

To manage these units, you use the `systemctl` command. It’s like the manager of all these workers, operators, and watchmen. You can use it to start, stop, restart, and check the status of these units. Display available unit types with the systemctl -t help command

```sql
# systemctl -t help

Available unit types:
service
mount
swap
socket
target
device
automount
timer
path
slice
scope
```

---

### How to Manage Daemons

To manage daemons in Linux, you can use the `systemctl` command. Here are some common operations you can perform:

* **Check the** `STATUS` **of Service and** `START, STOP, RESTART, RELOAD, ENABLE, DISABLE, MASK, UNMASK` **a service**:
    

```sql
# systemctl status  <SERVICE-NAME>
# systemctl start   <SERVICE-NAME>
# systemctl stop    <SERVICE-NAME>
# systemctl restart <SERVICE-NAME>
# systemctl reload  <SERVICE-NAME>
# systemctl enable  <SERVICE-NAME>
# systemctl disable <SERVICE-NAME>
# systemctl mask    <SERVICE-NAME>
# systemctl unmask  <SERVICE-NAME>
```

These commands are used to manage services (or daemons) in Linux using `systemd`. Here’s what each command does:

* `systemctl status <SERVICE-NAME>`: This command displays the current status of a service. It shows whether the service is running, stopped, or in any other state.
    
* `systemctl start <SERVICE-NAME>`: This command starts a service. If the service is already running, it does nothing.
    
* `systemctl stop <SERVICE-NAME>`: This command stops a running service.
    
* `systemctl restart <SERVICE-NAME>`: This command first stops and then starts a service. It’s useful when you’ve made configuration changes that need to be picked up by the service.
    
* `systemctl reload <SERVICE-NAME>`: This command asks a service to reload its configuration. Not all services support this, but for those that do, it’s a way to pick up configuration changes without the disruption of stopping and starting the service.
    
* `systemctl enable <SERVICE-NAME>`: This command enables a service to start at boot time.
    
* `systemctl disable <SERVICE-NAME>`: This command disables a service from starting at boot time.
    
* `systemctl mask <SERVICE-NAME>`: This command completely disables a service - it cannot be started manually or at boot time.
    
* `systemctl unmask <SERVICE-NAME>`: This command removes the mask, allowing a service to be started manually or at boot time. It’s used when you want to re-enable a service that was previously masked.
    

---

### Difference between "restart VS reload" & "mask VS unmask" the services in rhel Linux.

<mark>RESTART</mark>

When you **restart** a service, it first stops the current running instance of the service. The system sends a `SIGTERM (A polite way to stop a process)` signal to the service to terminate it. If the service does not stop within a certain time frame, a `SIGKILL (A forceful way to stop the process)` signal is sent to force the termination. After the service is stopped, it is then started again, hence the term “restart”. Each running process on a system is assigned a unique process ID (PID). When the service is stopped, it no longer has a PID. Then, the service starts again and is assigned a new PID. If any changes have been made to the service’s configuration files, these are read and applied when the service starts again. For example:

```sql
# systemctl restart httpd
```

<mark>RELOAD</mark>

On the other hand, **reload** tells the running service to check its configuration files again and apply any changes without actually stopping and starting the service. When you **reload** a service, the system sends a `SIGHUP (Reload process configurations files)` signal to the service. This signal instructs the service to reload its configuration files while continuing to run. This allows the service to apply any changes made in its configuration files without interrupting its operation. For example:

```sql
# systemctl reload httpd
```

<mark>MASK</mark>

**Masking** a service means to link it to `/dev/null`, making it impossible to start the service. This is used when you don’t want a certain service to run at all, even if another service tries to start it.

* let’s consider a case study involving the `firewalld` and `iptables` services in CentOS/RHEL, which is a common scenario in real-world Linux system administration.
    
* CentOS/RHEL 7 has both `firewalld` and `iptables` services for firewall management. However, it is recommended to use only one at a time to prevent conflicts. Let’s say you decide to use `firewalld` and want to prevent `iptables` from running even accidentally. Here’s how you can do it:
    
* **Mask the** `iptables` service:
    
    ```sql
    # systemctl mask iptables
    ```
    
    This command prevents the `iptables` service from being started, even by other services. Now Check the status of the `iptables` service:
    
    ```sql
     # systemctl status iptables
    ```
    
    You should see a message indicating that the service is masked. Now, suppose you later decide that you want to use `iptables` instead of `firewalld`. Here’s how you can unmask the `iptables` service:
    

<mark>UNMASK</mark>

**Unmasking** a service undoes the masking. If you’ve previously masked a service but now you want it to be able to start, you would unmask it.

* **Unmask the** `iptables` service:
    
    ```sql
    # systemctl unmask iptables
    ```
    
* This command removes the mask from the `iptables` service, allowing it to be started.Check the status of the `iptables` service:
    
* ```sql
    # systemctl status iptables
    ```
    
    You should see a message indicating that the service is loaded and inactive (dead), meaning it can now be started.
    

This case study illustrates how the `mask` and `unmask` commands can be used to control which services are allowed to run on a CentOS/RHEL system, providing a powerful tool for system administrators. It’s important to note that while this example uses `firewalld` and `iptables`, the same principles apply to any services managed by `systemd`.

---

### Details in "systemctl status SERVICE"

```sql
# systemctl status sshd
● sshd.service - OpenSSH server daemon
     Loaded: loaded (/usr/lib/systemd/system/sshd.service; enabled; vendor preset: enabled)
     Active: active (running) since Thu 2024-02-15 10:47:44 IST; 2h 55min ago
       Docs: man:sshd(8)
             man:sshd_config(5)
   Main PID: 5746 (sshd)
      Tasks: 1 (limit: 22833)
     Memory: 1.7M
        CPU: 17ms
     CGroup: /system.slice/sshd.service
             └─5746 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"

Feb 15 10:47:43 server1.example.com systemd[1]: Starting OpenSSH server daemon...
Feb 15 10:47:44 server1.example.com sshd[5746]: Server listening on 0.0.0.0 port 22.
Feb 15 10:47:44 server1.example.com sshd[5746]: Server listening on :: port 22.
Feb 15 10:47:44 server1.example.com systemd[1]: Started OpenSSH server daemon.
```

The `systemctl status SERVICE` command provides a detailed report about the specified service. Here’s what each line in the output means:

* `● sshd.service - OpenSSH server daemon`: This line shows the name of the service and a brief description of it.
    
* `Loaded: loaded (/usr/lib/systemd/system/sshd.service; enabled; vendor preset: enabled)`: This line shows the path to the service’s unit file, whether the service is enabled to start at boot, and the vendor preset status.
    
* `Active: active (running) since Thu 2024-02-15 10:47:44 IST; 2h 55min ago`: This line shows the current state of the service, when it entered this state, and how long it has been in this state.
    
* `Docs: man:sshd(8) man:sshd_config(5)`: This line provides references to the man pages related to the service.
    
* `Main PID: 5746 (sshd)`: This line shows the main Process ID (PID) for the service.
    
* `Tasks: 1 (limit: 22833)`: This line shows the current number of tasks or threads the service is running and the limit set on them.
    
* `Memory: 1.7M`: This line shows the current memory consumption of the service.
    
* `CPU: 17ms`: This line shows the CPU time consumed by the service.
    
* `CGroup: /system.slice/sshd.service └─5746 "sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups"`: This line shows the control group hierarchy of the service and the commands being run under this service.
    
* `log entries from the service:` The lines starting with the date (e.g., `Feb 15 10:47:43` [`server1.example.com`](http://server1.example.com) `systemd[1]: Starting OpenSSH server daemon...`) are log entries from the service. They provide a chronological account of what the service has been doing. In this case, it shows when the OpenSSH server daemon started and that it’s listening on ports 22 for both IPv4 and IPv6.
    

---

### Other Important "systemd management" command

Here are some important `systemctl` commands and their uses:

1. **Change the default system target (run-level)**: This command is used to change the default system target (run-level).
    

```sql
# systemctl set-default [target]
```

```sql
# systemctl set-default graphical.target
# systemctl isolate graphical.target
# systemctl set-default multi-user.target
# systemctl isolate multi-user.target
```

1. **List all installed unit files and their states**: This command is used to list all installed unit files and their states.
    
    ```sql
    # systemctl list-unit-files
    # systemctl list-unit-files -
    ```
    
2. **List the dependencies of a specific unit**: This command is used to list the dependencies of a specific unit.
    
    ```sql
    # systemctl list-dependencies [unit]
    ```
    
3. **List all active sockets**: This command is used to list all active sockets.
    
    ```sql
    # systemctl list-sockets
    ```
    
4. **List all active systemd jobs**: This command is used to list all active systemd jobs.
    
    ```sql
    # systemctl list-jobs
    ```
    

**Show the status of all loaded and active systemd units**: This command is used to show the status of all loaded and active systemd units.

```sql
# systemctl list-units
```

---

### Interview Questions & Answers Related to "systemd management"

1. **What is systemd?**
    
    **Answer:** Systemd is a system and service manager for Linux operating systems. It initializes and manages/maintains system processes after the Linux kernel has booted up.
    
2. **What is the role of a service in a systemd context?**
    
    **Answer:** A service is a program that runs as a background process. In a systemd context, services are defined by service unit files, and systemd starts them and manages their state according to these files.
    
3. **How do you check the status of a service using systemd?**
    
    **Answer:** You can check the status of a service using the command `systemctl status service_name`.
    
4. **How do you start, stop, or restart a service?**
    
    **Answer:** You can use the commands `systemctl start service_name`, `systemctl stop service_name`, and `systemctl restart service_name` respectively.
    
5. **How do you enable or disable a service to start at boot?**
    
    **Answer:** You can use the commands `systemctl enable service_name` and `systemctl disable service_name` respectively.
    
6. **What is a unit file in systemd?**
    
    **Answer:** A unit file is a configuration file that defines the properties of system resources managed by systemd, such as services, sockets, devices, etc.
    
7. **What is the difference between** `systemctl reload` and `systemctl restart`?
    
    **Answer:** `systemctl reload` only reloads the configuration file of the service, while `systemctl restart` will stop and then start the service again.
    
8. **What is a socket in systemd?**
    
    **Answer:** A socket is a special file used for inter-process communication, which can also be managed by systemd. Socket units in systemd have a `.socket` extension.
    
9. **What is the target in systemd and how is it used?**
    
    **Answer:** A target is a unit that groups together other units, similar to how runlevels group services in SysVinit. They are used to create a system state or mode defined by the services they group.
    
10. **How do you list all active (running) services in systemd?**
    
    **Answer:** You can use the command `systemctl --type=service --state=running`.
    
11. **What is** `journald` in the context of systemd?
    
    **Answer:** `journald` is a part of systemd that provides a centralized management of system logs.
    
12. **How do you see the log of a particular service using systemd?**
    
    **Answer:** You can use the command `journalctl -u service_name`.
    
13. **What is the cgroup in systemd?**
    
    **Answer:** Cgroup is a Linux kernel feature to limit, police and account the resource usage for a set of processes. In systemd, it’s used to track the processes that systemd starts.
    
14. **How do you mask a service in systemd?**
    
    **Answer:** You can use the command `systemctl mask service_name`. Masking a service makes it impossible to start it.
    
15. **What is the difference between** `systemctl mask` and `systemctl disable`?
    
    **Answer:** `systemctl disable` prevents the service from starting at boot, but allows manual starting, while `systemctl mask` prevents the service from starting altogether, both at boot and manually.
    
16. **What is** `systemctl daemon-reload` used for?
    
    **Answer:** `systemctl daemon-reload` is used to reload the systemd manager configuration. This includes reloading all unit files and recreating the entire dependency tree. This is typically done after creating or modifying a unit file.
    
17. **How do you check which version of systemd you are running?**
    
    **Answer:** You can use the command `systemctl --version`.
    
18. **Question:** What is a daemon in the context of operating systems?
    
    **Answer:** A daemon is a type of program on Unix-like operating systems that runs silently without users direct interactions in the background, rather than under the direct control of a user, waiting to be activated by the occurrence of a specific event or condition.
    
19. **Question:** How does a service differ from a daemon?
    
    **Answer:** A service is a program or a set of programs that perform system-level operations in an operating system. A daemon is a type of service that runs in the background and is not directly interacted with by the user.
    
20. **Question:** What is the role of `systemd` in managing services and daemons? **Answer:** `systemd` is a system and service manager for Linux operating systems. It initializes and manages/maintains/tracks system services and daemons, both during startup and while the system is running.
    
21. **Question:** Explain the difference between `service` and `systemctl` commands.
    
    **Answer:** Both `service` and `systemctl` are used to interact with system services. However, `service` is a more legacy command and is being replaced by `systemctl`, which provides more detailed status information and is more consistent in its syntax.
    
22. **Question:** How can you enable or disable a service to start on boot? **Answer:** You can use `systemctl enable serviceName` to have a service start at boot, and `systemctl disable serviceName` to prevent a service from starting at boot.
    
23. **Question:** How would you check the status of a service in Windows? **Answer:** In Windows, you can check the status of a service through the Services management console (`services.msc`), or by using the `sc query` command in the command prompt.
    
24. **Question:** How can you create a custom service in Linux?
    
    **Answer:** In Linux, you can create a custom service by writing a service unit file and placing it in the `/etc/systemd/system` directory. The unit file will specify how the service should start, stop, and otherwise operate.
    
25. **Question:** What are the potential security implications of running a service/daemon as root?
    
    **Answer:** Running a daemon as root can be a security risk because if the daemon is compromised, it could give an attacker full control over the system. It’s generally recommended to run daemons under non-privileged user accounts when possible.
    
26. **Question:** How does `systemd` handle dependencies between services? **Answer:** `systemd` handles dependencies through a directive in the service unit file called `After` or `Before`, which ensures that one service starts after or before another. It also uses `Wants` or `Requires` to specify if a service should continue running if its dependencies fail.
    
27. **Question:** What is the role of the `journalctl` command in relation to services and daemons?
    
    **Answer:** `journalctl` is used to query and display messages from the systemd journal, which includes logs from services and daemons.
    
28. **Question:** How can you configure a service to automatically restart if it crashes?
    
    **Answer:** In the service’s unit file, you can set the `Restart` directive to `always` or `on-failure` to have `systemd` automatically restart the service if it crashes.