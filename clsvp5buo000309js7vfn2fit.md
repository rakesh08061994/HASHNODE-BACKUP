---
title: "Linux Networking: A Detailed Guide for the Curious Mind"
datePublished: Wed Feb 21 2024 11:14:01 GMT+0000 (Coordinated Universal Time)
cuid: clsvp5buo000309js7vfn2fit
slug: linux-networking-a-detailed-guide-for-the-curious-mind
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1708439683209/23857688-63e1-4f14-bf0c-9863faeb1132.png
tags: linux, devops, networking, networking-for-beginners

---

---

### What is a Network & Networking?

A network is a collection of computing devices (Ex:- Mobile, Computers, IoT Devices, Servers) connected via a communication medium (Wired, Wireless) to exchange information and resources while networking is the practice of creating, maintaining, securing, and troubleshooting this network.

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><code>What is computer networking?</code> Computer networking is like a web of computers that can talk to each other and share stuff. They use a set of rules, known as protocols, to send information using wires or wireless technologies.</div>
</div>

---

### **How does a computer network work?**

A computer network is a system that allows multiple computing devices (known as nodes) to connect and communicate with each other. This communication is facilitated through various mediums such as wires, optical fibers, or wireless links.

The basic building blocks of a computer network are nodes and links. A node can be a device for data communication like a modem, router, or a data terminal like a computer. Links in computer networks can be defined as wires or cables or free space of wireless networks.

Each device in a network has a unique IP Address that helps in identifying the device. Protocols, which are sets of rules, help in sending and receiving data via the links that allow computer networks to communicate. We will talk about IP address and stuff later.

---

### **What are two types of computer network architecture?**

There are two main types:

1. `Client-server architecture:` Here, some nodes (servers) provide resources to other nodes (clients). Clients can talk to each other but don’t share resources.
    
2. `Peer-to-Peer (P2P) architecture:` Here, all computers have the same powers. There’s no central server. Each device can act as a client or server and share resources with the network.
    

---

### **What is network topology?**

**Network Topology** is like a blueprint of a network. It shows how different devices such as computers, routers, and servers are connected to each other.

Here are the different types of network topologies:

1. `Point-to-Point Topology:` This is the simplest form where two devices are directly connected. It’s like a direct phone call between two people. For example, a satellite dish receiving a signal from a satellite is a point-to-point connection.
    
2. `Mesh Topology:` In this type, every device is connected to every other device. It’s like a group where everyone is friends with everyone else. This is often used in wireless networks where each device can communicate with every other device directly.
    
3. `Star Topology:` Here, all devices are connected to a central hub. It’s like a wheel where the hub is the center and the devices are the spokes. This is commonly used in home networks where all devices connect to a central router.
    
4. `Bus Topology:` All devices are connected through a single cable, known as the backbone. It’s like a bus route where all stops (devices) are located along the route. This was commonly used in old Ethernet networks.
    
5. `Ring Topology:` Devices are connected in a circle, and data moves in one direction from one device to another. It’s like a circular conveyor belt where packages (data) can hop on at one station and hop off at another. This is used in some types of office networks.
    
6. `Tree Topology:` This is a combination of star and bus topologies and looks like a tree with branches. This is often used in wide area networks (WANs) that span large distances, like a network of a large company with many branches.
    
7. `Hybrid Topology:` This is a combination of two or more different types of topologies. This is often used in large businesses where different departments have different needs.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708424631297/9a730f36-87fc-4ba0-b63c-f061f2b7e5fc.png align="center")

---

### **What are the types of enterprise computer networks?**

Computer networks can vary in size and complexity:

* `Personal Area Network (PAN):` A network that connects devices over a very short distance, often within a range of 10 meters. For example, a smartphone connected to a wearable device.
    
* `Local Area Network (LAN):` A network that connects devices over a short distance, such as within a building or a campus.
    
* `Metropolitan Area Network (MAN):` A network that covers a larger geographic area, such as a city.
    
* `Wide Area Network (WAN):` A network that covers a large geographic area, such as a country or the entire world. The Internet is an example of a WAN.
    
* `Service provider networks:` An Internet Service Provider (ISP) is an example of a service provider network. ISPs are organizations that provide services for accessing, using, managing, or participating in the Internet. They can be organized in various forms, such as commercial, community-owned, non-profit, or privately owned. ISPs provide internet access, internet transit, domain name registration, web hosting, and colocation.
    
* `Cloud networks:` A Virtual Private Cloud (VPC) is an example of a cloud network. A VPC is a virtual network dedicated to your AWS account. It is logically isolated from other virtual networks in the AWS Cloud. You can specify an IP address range for the VPC, add subnets, add gateways, and associate security groups. A subnet is a range of IP addresses in your VPC. Amazon VPC lets you define and launch AWS resources in a virtual network that you control. You can customize your VPC by choosing your own IP address range, creating subnets, and configuring route tables, and secure and monitor your connections with security groups and firewalls.
    

---

### The main components of a computer network

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">What do you mean by computer network components?</div>
</div>

Computer network components are the major parts that are needed to install a network according to network topology architectural setup. The design of a network for any organization is indeed influenced by the choice of network components and network topologies. These components are crucial in the design of a computer network architecture as they dictate the layout, communication protocols, and connectivity patterns of network systems.

`1. NIC (Network Interface Card):`

This is a piece of hardware that connects a computer to a network. It can handle data transfer rates from 10 to 1000 Mb/s. There are two types:

* **Wired NIC**: This is inside the computer’s motherboard and uses cables to transfer data.
    
* **Wireless NIC**: This has an antenna for wireless connections. For example, laptops have wireless NICs.
    

`2. HUB:`

* A Hub is a connector that connects wires coming from different sides.
    
* It operates only on the physical layer (Layer 1) of the OSI model.
    
* It is also known as a repeater as it transmits signals to every port except the port from where the signal is received.
    
* Hubs are not intelligent in communication and processing information for the 2nd and 3rd layer.
    

`3. Switch:`

* A Switch is a point-to-point communication device that operates on both the physical and data link layers (Layer 1 and Layer 2) of the OSI model.
    
* It can inspect data packets as they are received, determine the source and destination device of each packet, and forward them appropriately.
    
* By delivering messages only to the connected device intended, a network switch conserves network bandwidth and offers generally better performance than a hub.
    

`4. Router:`

* A Router is a device that forwards data packets between computer networks, creating an overlay internetwork. It operates on the third layer (Network Layer) of the OSI model.
    
* Routers use headers and forwarding tables to determine the best path for forwarding the packets, and they use protocols such as ICMP to communicate with each other and configure the best route between any two hosts.
    
* Unlike access points and modems, routers have the ability to connect two or more logical subnets, which do not necessarily map one-to-one to the physical interfaces of the router.
    

`5. Access Point:`

* An Access Point, on the other hand, is a device that allows wireless devices to connect to a network. It serves as a central transmitter and receiver of wireless radio signals.
    
* Access points are used for extending the wireless coverage of an existing network and for increasing the number of users that can connect to it. Unlike a router, it does not handle traffic routing across multiple networks.
    

`6. Modem:`

* A Modem is a device that connects your home, usually through a coax cable connection, to your Internet Service Provider (ISP), like Jio, Airtel, Idea, or others.
    
* The modem takes signals from your ISP and translates them into signals your local devices can use, and vice versa. Unlike routers and access points, modems do not manage network traffic - they simply provide a pathway for it.
    

`7. Cables and Connectors:`

These are used for transmitting signals. The three types of cables used are twisted pair cable, coaxial cable, and fiber-optic cables.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708424269993/3d803daa-a299-46ea-871a-6261d5f5fa3b.png align="center")

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Let's design our first network architecture.</div>
</div>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708425197966/47e54f2c-2a8e-412e-8485-37f1e2104406.png align="center")

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">If you want to simulate and design your personal network architecture, please use the ‘Cisco Packet Tracer Network Tool’. The student version is available free of cost. Download link: <a target="_blank" rel="noopener noreferrer nofollow" href="https://www.packettracernetwork.com/download/download-packet-tracer.html" style="pointer-events: none">Click Here</a></div>
</div>

---

### The Logical Terminology of Networking

1. `IP Address`
    
    Any digital device that is connected to the internet is assigned an address known as an IP address, which can be obtained in two ways: statically or dynamically. An IP (Internet Protocol) address is a unique numerical label assigned to each device participating in a computer network that uses the Internet Protocol for communication. It’s like a house address in the digital world for your system, allowing computers to send and receive information over the internet.
    
    ```plaintext
    C:\Users\RakaModify-PC> ipconfig
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708430286247/13bf4b10-b2a3-4a0e-b3a1-0c81103d7088.png align="center")

1. `Versions Types of IP addresses:`
    

* `IPv4:` This is the most commonly used version. An IPv4 address consists of four numbers separated by dots, each ranging from 0 to 255. For example, 192.168.1.1. Each number can be represented by a group of 8-digit binary digits, making the whole IPv4 binary address represented by 32-bits of binary digits.
    
* `IPv6:` This version was introduced to deal with the exhaustion of IPv4 addresses. An IPv6 address is longer and can generate a vast number of unique IP addresses. It uses 128 bits for the IP address, which was standardized in 1998.
    

1. `Static or dynamic IP:`
    

* `Static:` These are permanent IP addresses typically assigned manually by an administrator. They are fixed or permanent and do not change over time.
    
* `Dynamic:` These are temporary and are assigned each time on lease, and a device accesses the Internet through DHCP `(Dynamic Host Configuration Protocol)` server. Your internet activity goes through your service provider, and they route it back to you, using your IP address. Your IP address can change, for example, turning your router on or off can change your IP Address.
    

1. `Private IP (Virtual IP) vs. public IP (Real IP)`
    
    * `Private IP Address:` This is the IP address that is used to communicate within the same network. It is assigned by the router to each device on the network. Private IP addresses are more secure as they can only be traced within the local network and are not visible online.
        
    * `Public IP Address:` This is the IP address that is used to communicate outside the network. It is assigned by the Internet Service Provider (ISP). Public IP addresses can be traced back to the ISP, revealing the geographical location. They are visible online and are unique on the internet.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708432536326/8769afce-e2fb-4dd8-8031-9d44b1c3e9ce.png align="center")

1. `Logical Address VS Physical Address`
    
    * `Physical Address:` This is also known as the MAC (Media Access Control) address or link address. It is the address of a node as defined by its LAN or WAN. It’s used by the data link layer and is the lowest level of addresses. Physical addresses are unique to each device and are used to identify devices in the same network. However, they can only be used in local networks and not between different networks.
        
    * `Logical Address:` Also referred to as IP (Internet Protocol) address, it is used in the Network layer. This address facilitates universal communication that is not dependent on the underlying physical networks. There are two types of IP addresses – IPv4 and IPv6. Logical addresses provide a layer of abstraction that allows processes to access memory without knowing the physical memory location.
        

6\. `What is MAC (Physical Address, Hardware Address) & NIC (LAN Card, Network Adapter)`

* `NIC (Network Interface Card):` It’s a hardware component, also known as a LAN card or network adapter, that enables a computer to connect to a network. Each NIC is assigned an IP address when connected to a network, allowing the system to be identified and communicate with other systems on the network.
    
* `MAC (Media Access Control) Address:` This is a unique 48-bit hardware number embedded & assigned to a NIC by the manufacturer. It’s used for network communication within a network segment. Unlike an IP address, which can change based on network assignment, a MAC address is a unique, physical address embedded into the device. It helps in uniquely identifying a system in the world.
    
    <div data-node-type="callout">
    <div data-node-type="callout-emoji">💡</div>
    <div data-node-type="callout-text">In windows try this command to see MAC address: <code>ipconfig /all</code></div>
    </div>
    
    ```plaintext
    C:\Users\Rakesh-PC>  ipconfig /all
    ```
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708434312997/37ac7167-20ef-4c37-9cf1-be8bb1f59a5c.png align="center")

1. `ISP (Internet Service Provider)`
    
    ISP, or Internet Service Provider, is a company that gives people access to the internet. Customers pay a fee to the ISP, which can change based on how much data they use or the data plan they choose. ISPs are also called Internet Access Providers or online service providers. If you want to connect to the internet, you need an ISP. Ex: Idea, Airtel, Jio etc.
    
2. [`DNS Server`](https://www.rakamodify.online/understanding-dns-servers-the-internets-phonebook-made-simple)`(Domain Name Server)`
    
    The Domain Name System (DNS) is like the phonebook of the Internet. When users type domain names such as ‘[google.com](http://google.com)’ or ‘[nytimes.com](http://nytimes.com)’ into web browsers, DNS is responsible for finding the correct IP address for those sites. DNS servers are machines dedicated to answering DNS queries.
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">If you want to know more about "DNS Server" Try this article on <a target="_blank" rel="noopener noreferrer nofollow" href="https://www.rakamodify.online" style="pointer-events: none">RakaModify</a>. Article Link: <a target="_blank" rel="noopener noreferrer nofollow" href="https://www.rakamodify.online/understanding-dns-servers-the-internets-phonebook-made-simple" style="pointer-events: none">What is DNS Server?</a></div>
</div>

8\. `NAT (Network Address Translator) & How NAT work?`

* NAT, which stands for Network Address Translation, is like a translator for internet addresses. It allows multiple devices on a local network (like the devices connected to your home Wi-Fi) to connect to the internet using just one public IP address. When a device on your network wants to access the internet, NAT changes the device’s private IP address to a public one. This is because private IP addresses can’t be used on the internet.
    
* When the internet sends data back, NAT changes the public IP address back to the private one. This way, all devices on your network can share the same public IP address but still have their own unique private addresses inside the network. This process is crucial for keeping your network secure and efficient.
    

1. `Client Machine & Server Machine`
    

* `A client machine` is like a regular computer that we use every day, such as a smartphone or a laptop. It’s designed for simple tasks and has basic hardware and software.
    
* `A server machine`, on the other hand, is a more powerful version of a client machine. It has high-end hardware and software configurations. Its main job is to provide services like web hosting (HTTP), secure shell access (SSH), database management, and storage to client machines over a network.
    
    <div data-node-type="callout">
    <div data-node-type="callout-emoji">💡</div>
    <div data-node-type="callout-text">A <strong>machine</strong> can be a <strong>client</strong> or a <strong>server</strong>. A client machine uses services, and a server machine provides services.</div>
    </div>
    

---

### IP Address Classification & Subnetting through Netmasking.

`Classes of IPv4`

IPv4 addresses are divided into five classes: A, B, C, D, and E. Each class has a range of IP addresses and is used for different types of networks:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708441273394/ba91ff4f-34d9-4da7-9702-a7b0806b12a9.png align="center")

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">Please note that Class D and E are reserved for special uses. Class D is used for multicasting<a target="_blank" rel="noopener noreferrer nofollow" href="https://t4tutorials.com/ip-subnetting-techniques-and-class-a-b-c-d-and-e/" style="pointer-events: none">,</a> while Class E is reserved for experimental use. Therefore, they do not have a private IP range, subnet mask, or a specific number of networks or hosts per network.</div>
</div>

* `Class A:` This class is used for very large networks, such as multinational corporations. The IP addresses in Class A range from 1.0.0.0 to 126.0.0.0. The first octet (the first set of numbers before the dot) is used for the network ID, and the remaining three octets are used for the host ID. This means there can be 126 networks (2^7 - 2) and 16,777,214 hosts (2^24 - 2) in each network. 127.0.0.1 is save reserved for self localhost address.
    
* `Class B:` This class is used for medium-sized networks, like large universities. The IP addresses in Class B range from 128.0.0.0 to 191.255.0.0. The first two octets are used for the network ID, and the remaining two octets are used for the host ID. This allows for 16,384 networks (2^14) and 65,534 hosts (2^16 - 2) in each network.
    
* `Class C:` This class is used for small networks, like small businesses. The IP addresses in Class C range from 192.0.0.0 to 223.255.255.0. The first three octets are used for the network ID, and the last octet is used for the host ID. This allows for 2,097,152 networks (2^21) and 254 hosts (2^8 - 2) in each network.
    
* `Class D and E:` These classes are reserved for special uses, such as multicasting and research.
    

---

### What is Subnetting/Netmasking?

Subnetting is a method for dividing a network into smaller, more manageable pieces. This is done by taking bits from the host portion of the IP address and using them to create a subnet. A subnet mask is used to determine which part of the IP address is the network section and which part is the host section.

For example, consider an IP address of `192.168.1.0` with a subnet mask of `255.255.255.0`. The `255` in the subnet mask tells us that the corresponding octet in the IP address is all part of the network address. So in this case, `192.168.1` is the network address, and the last part (represented by `0`) is left for hosts on that network.

`Importance of Subnetting/Netmasking`

* Subnetting is important for several reasons:
    
* `Efficiency:` It allows for more efficient use of IP addresses. By dividing a network into subnets, you can ensure that IP addresses are not wasted.
    
* `Performance:` Subnetting can reduce network congestion. By confining network traffic to a single subnet, you can prevent that traffic from affecting other subnets.
    
* `Security:` Subnetting can improve network security. By isolating different parts of the network into different subnets, you can limit the impact of a security breach. If one subnet is compromised, the others remain secure.
    

---

### **Case Study: To Understand Network & Netmask**

> TechCo is a small company that is divided into five key departments: HR, Tech, Accounts, Sales, and Others. Each department is equipped with a different number of computers to meet its specific needs. The HR department has 5 computers, Accounts has 15, Tech has 60, Sales has 30, and Others has 11.
> 
> To ensure smooth inter-departmental communication, TechCo purchased a “Type-C” network range. The challenge was to divide this network range efficiently among the five departments, a process known as subnetting. The goal was to provide each department with enough network addresses for its computers, while minimizing the number of unused addresses.
> 
> This case study will explore how TechCo successfully implemented subnetting to optimize its network division across the five departments in a simple and understandable manner.
> 
> **<mark>Answer:</mark>** TechCo, a small company, is divided into five sub-departments: HR, Tech, Accounts, Sales, and Others. Each department has a different number of computers: HR has 5, Accounts has 15, Tech has 60, Sales has 30, and Others has 11.
> 
> To establish an efficient network among these departments, TechCo purchased a Type-C network with a range of `192.168.25.0 - 192.168.25.255` and divided it into subnets. The division of the network among the departments is as follows:
> 
> * The **Network Address** is the first IP in the range, which is **192.168.25.0**.
>     
> * The **Broadcast Address** is the last IP in the range, which is **192.168.25.255**.
>     
> * The Self Loop Localhost Address is the IP range, which is 127.0.0.1
>     

| Department | No. of Computers | Subnet Size | Unused Addresses | IP Subnetting |
| --- | --- | --- | --- | --- |
| HR | 5 | 8 | 3 | 192.168.25.1/8 to 192.168.25.5/8 |
| Accounts | 15 | 16 | 1 | 192.168.25.6/16 to 192.168.25.21/16 |
| Tech | 60 | 24 | 4 | 192.168.25.22/24 to 192.168.25.82/24 |
| Sales | 30 | 27 | 2 | 192.168.25.83/27 to 192.168.25.113/27 |
| Others | 11 | 28 | 5 | 192.168.25.114/28 to 192.168.25.125/28 |

> This case study demonstrates how TechCo efficiently divided its network among its departments, ensuring optimal use of resources.

---

### What is TCP/IP Networking Model

The TCP/IP network model is a simplified, four-layered set of communication protocols that describes how data communications are packetized, addressed, transmitted, routed, and received between computers over a network. Here’s a detailed explanation of each layer:

1. `Application Layer:` Each application has specifications for communication so that clients and servers can communicate across platforms. Common protocols include SSH, HTTPS (secure web), FTP (file sharing), and SMTP (electronic mail delivery).
    
2. `Transport Layer:` This layer uses TCP and UDP as transport protocols. TCP is a reliable connection-oriented communication, while UDP is a connectionless datagram protocol. Application protocols can use either TCP or UDP ports. When a packet is sent on the network, the combination of the service port and IP address forms a socket. Each packet has a source socket and a destination socket. This information can be used when monitoring and filtering network traffic.
    
3. `Internet Layer:` The Internet, or network layer, carries data from the source host to the destination host. The IPv4 and IPv6 protocols are Internet layer protocols. Each host has an IP address and a prefix to determine network addresses. Routers are used to connect networks.
    
4. `Link Layer:` The link, or media access, layer provides the connection to physical media. The most common types of networks are wired Ethernet (802.3) and wireless Wi-Fi (802.11). Each physical device has a Media Access Control (MAC) address, also known as a hardware address, to identify the destination of packets on the local network segment.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708508136187/e39671f2-f446-4b46-85b4-cfd70241ca5a.png align="center")
    

---

### **What is Ports & Sockets**

* Port = Running service address on the server
    
* IP Address = Your system's logical address on the internet
    
* Socket = IP address + Service Port
    

Why Sockets is important and useful?

* In a multitasking system, multiple services can run concurrently. Each device on the internet is identified by an IP address, which can be either static or dynamic. On a system level, while all services share the same IP address, they run individually on specific ports. For instance, in a network, your system might be assigned an IP address like 192.168.10.25/24. On this system, multiple servers could be running concurrently, each on its own port. Examples include a database server on port 3306, SSH on port 22, a web server on ports 443 and 80, and NFS on port 2049.
    
* A socket is one endpoint of a two-way communication link between two programs running on the network. When user “A” wants to send data to user “B” at a different location, the data is broken down into smaller data packets. These packets follow the TCP/IP protocol for transmission. Each packet contains data and the destination socket information (IP address and port number). The socket itself is an interface for sending and receiving data.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708510470114/91021ca9-ccfa-4e50-a02d-212b13f6284e.png align="center")

```plaintext
# vim /etc/services  -------? Showing all ports
# netstat -tulpn     --------? Showing open running service port
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708510367678/b8f4c92f-9771-4819-83ef-1e3b967a108c.png align="center")

* A `socket` is the combination of an `IP address` and a `port number`. When a packet is sent on the network, it has a source socket and a destination socket. The socket helps in identifying the source and destination of the packet, which is crucial for routing and delivering the packet correctly. This concept is used in the transport layer of the TCP/IP model for monitoring and filtering network traffic
    

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text">In a system total of 65536 ports are available. You can find port range on location <code>/etc/services.</code></div>
</div>

---

### NetworkManager & Configuration Setup

1. `What is NetworkManager?` NetworkManager is a service that monitors and manages a system’s network settings. It is designed to simplify and automate the control of network connections.
    
    ```plaintext
    # systemctl status NetworkManager.service
    ```
    
2. `Purpose of NetworkManager:` The purpose of NetworkManager is to keep track of network devices and connections, and to ensure that network access is available when needed and not used when not needed.
    
3. `Interaction with NetworkManager:` Users can interact with the NetworkManager service via the command line `(nmcli)` or with graphical tools `(nmtui)`. In the GNOME graphical environment, a Notification Area applet displays network configuration and status information that is received from the NetworkManager daemon.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1708666634390/d918424e-1c80-4a05-9995-d941fd2ee696.jpeg align="center")
    
4. `Configuration Files:` The configuration files for the service are stored in the `/etc/NetworkManager/system-connections/` directory.
    
5. `Network Devices and Connections:` A network device is a physical or virtual network interface that provides for network traffic. A connection is a collection of related configuration settings for a single network device, also known as a network profile. Each connection must have a unique name or ID, which can match the device name that it configures.
    
6. `Multiple Connection Configurations:` A single device can have multiple connection configurations and switch between them, but only one connection can be active per device. For example, a laptop wireless device might configure a fixed IP address for use at a secure work site in one connection, but might configure a second connection with an automated address and a virtual private network (VPN) to access the same company network from home.
    
7. `Changes in Red Hat Enterprise Linux 8:` Starting in Red Hat Enterprise Linux 8, ifcfg format configuration files and the `/etc/sysconfig/network-scripts/` directory are deprecated. NetworkManager now uses an INI-style key file format, which is a key-value pair structure to organize properties. NetworkManager stores network profiles in the `/etc/NetworkManager/system-connections/` directory. For compatibility with earlier versions, ifcfg format connections in the `/etc/sysconfig/network-scripts/` directory are still recognized and loaded.
    
8. `How to View Network Information?`
    
    ```plaintext
    # nmcli connection show
    # nmcli connection show <connection-name>
    # nmcli connection show --active
    # nmcli device show
    # nmcli device show <device-name>
    # nmcli device status
    ```
    
9. `How to Add a Network Connection?`
    
    * Uses Manual Connection build (Not autoconnect on startup)
        
        ```plaintext
        # nmcli con add con-name test type ethernet ifname ens160 \
        ipv4.addresses 192.168.199.130/24 ipv4.dns 8.8.8.8 \
        ipv4.gateway 192.168.199.254 connection.autoconnect yes ipv4.method manual    
        ```
        
    * connection uses a DHCP service and has the device autoconnect on startup.
        
        ```plaintext
        # nmcli con add con-name dynamo type ethernet \
        ifname ens160 connection.autoconnect yes ipv4.method auto/dhcp
        ```
        
10. `How to Modify an existing Network Connections?`
    
    * Modify through Command Line interface
        
        ```plaintext
        # nmcli con mod test ipv4.addresses 192.0.2.2/24 \
        ipv4.gateway 192.0.2.254 connection.autoconnect yes
        ```
        
    * Modify through direct profile configuration file
        
        ```plaintext
        # vim /etc/NetworkManager/system-connections/test.nmconnection
        # systemctl restart NetworkManager
        ```
        
        <div data-node-type="callout">
        <div data-node-type="callout-emoji">💡</div>
        <div data-node-type="callout-text">Some settings can have multiple values. A specific value can be added to the list or deleted from the connection settings by adding a plus (+) or minus (-) symbol to the start of the setting name. If a plus or minus is not included, then the specified value replaces the setting's current list. The following example adds the 8.8.4.4 DNS server to the test connection.</div>
        </div>
        
        ```plaintext
        # nmcli con mod test +ipv4.dns 8.8.4.4
        ```
        
11. `How to work with connection profiles?`
    
    ```plaintext
    # nmcli connection show
    # nmcli connection up <connection-name>
    # nmcli connection down <connection-name>
    # nmcli device disconnect <device-IF-name>
    # nmcli connection reload <connection-name>
    ```
    
12. `How to delete an Network Connection?`
    
    ```plaintext
    # nmcli con del <connection-name>
    ```
    

---

### Useful Network Management Commands

1. **ip**: This command provides information about every network interface. The correct usage is:
    
    ```bash
    ip a
    ip addr
    ```
    
2. **tracepath**: This command is used to find network delays. It does not require root privileges. The correct usage is:
    
    ```bash
    tracepath www.example.com
    ```
    
3. **ss**: This command is a replacement for the netstat command. It fetches information directly from the kernel userspace. The correct usage is:
    
    ```bash
    ss
    ```
    
4. **host**: This command shows the IP address for a hostname and the domain name for an IP address. It is also used for DNS lookups. The correct usage is:
    
    ```bash
    host -t A www.example.com
    ```
    
5. **hostname**: This command is used to view and set the system’s hostname. The correct usage is:
    
    ```bash
    hostname
    ```
    
6. **curl and wget**: These commands are used to download files from the internet using the command line interface (CLI). The correct usage is:
    
    ```bash
    curl -O https://example.com/path/to/file
    wget https://example.com/path/to/file
    ```
    
7. **mtr**: This command combines traceroute and ping commands. It regularly shows information related to the packets transferred using the ping time of all hops. The correct usage is:
    
    ```bash
    mtr www.example.com
    ```
    
8. **whois**: This command fetches all website-related information. The correct usage is:
    
    ```bash
    whois www.example.com
    ```
    
9. **tcpdump**: This command is widely used in network analysis. It analyses the traffic passing from the network interface and displays it. The correct usage is:
    
    ```bash
    tcpdump -i eth0
    ```
    
10. **tracepath**: This command traces the path that packets take from your computer to the destination address. The correct usage is:
    
    ```bash
    tracepath www.example.com
    ```
    
11. **tracepath6**: This command is similar to tracepath, but it is used for IPv6 addresses. The correct usage is:
    
    ```bash
    tracepath6 2001:db8:0:2::451
    ```
    
12. **dig**: This command is used to query DNS name servers for information about host addresses, mail exchanges, name servers, and related information. The correct usage is:
    
    ```bash
    dig www.example.com
    ```
    
13. **getent hosts**: This command retrieves entries from the specified administrative database. The correct usage is:
    
    ```bash
    getent hosts www.example.com
    ```
    
14. **ss -tulpn**: This command is used to dump socket statistics and displays listening sockets. The correct usage is:
    
    ```bash
    ss -tulpn
    ```
    
15. **ss -ta**: This command displays all non-listening sockets (that’s established connections). The correct usage is:
    
    ```bash
    ss -ta
    ```
    
16. **ss -lt**: This command displays only listening sockets. The correct usage is:
    
    ```bash
    ss -lt
    ```
    
17. **ip -br addr**: This command displays brief information about the IP addresses of all network interfaces. The correct usage is:
    
    ```bash
    ip -br addr
    ```
    
18. **netstat -tulpn**: This command displays network connections, routing tables, interface statistics, masquerade connections, and multicast memberships. The correct usage is:
    
    ```bash
    netstat -tulpn
    ```
    
19. **ip route**: This command displays the IP routing table. The correct usage is:
    
    ```bash
    ip route
    ```
    
20. **ip -6 route**: This command displays the IPv6 routing table. The correct usage is:
    
    ```bash
    ip -6 route
    ```
    
21. **ping**: This command sends ICMP ECHO\_REQUEST packets to network hosts. The correct usage is:
    
    ```bash
    ping www.example.com
    ```
    
22. **ping6**: This command is similar to ping, but it is used for IPv6 addresses. The correct usage is:
    
    ```bash
    ping6 ::1
    ```
    
23. **ping -c3 192.0.2.254**: This command sends exactly 3 ICMP ECHO\_REQUEST packets to the host with the IP address 192.0.2.254. The correct usage is:
    
    ```bash
    ping -c3 192.0.2.254
    ```
    
24. **ping6 2001:db8:0:1::1**: This command sends ICMP ECHO\_REQUEST packets to the IPv6 address 2001:db8:0:1::1. The correct usage is:
    
    ```bash
    ping6 2001:db8:0:1::1
    ```
    
25. **whois**: This command is used to retrieve domain name information from WHOIS servers. The correct usage is:
    
    ```bash
    whois example.com
    ```
    
26. **nslookup**: This command is used to query Internet domain name servers. The correct usage is:
    
    ```bash
    nslookup www.example.com
    ```
    
27. **ifconfig**: This command is used to display or configure a network interface. The correct usage is:
    
    ```bash
    ifconfig
    ```
    

---

### Reference Links:

* [https://aws.amazon.com/what-is/computer-networking/](https://aws.amazon.com/what-is/computer-networking/)