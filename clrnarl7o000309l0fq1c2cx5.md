---
title: "Understanding DNS Servers: The Internet’s Phonebook Made Simple"
datePublished: Sun Jan 21 2024 09:29:34 GMT+0000 (Coordinated Universal Time)
cuid: clrnarl7o000309l0fq1c2cx5
slug: understanding-dns-servers-the-internets-phonebook-made-simple
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1705822356864/23c65603-566e-41d0-a78e-3b0affd58475.png
tags: dns, linux, projects, computer-science, devops, networking, isp, linux-for-beginners, devops-articles, rakamodify

---

---

# What is DNS?

The Domain Name System (DNS) is a critical component of the Internet infrastructure that translates user-friendly domain names into numerical IP addresses. It’s often compared to a phone book for the Internet.

Here’s why DNS is important:

1. User-friendly: It allows users to interact with devices on the Internet using easy-to-remember domain names instead of having to remember long strings of numbers.
    
2. Smooth operation: DNS ensures the Internet works smoothly, loading the content we ask for quickly and efficiently.
    
3. Connectivity: If a DNS is not responding, you won’t be able to connect to other websites on the Internet.
    

For example, when you type [`www.google.com`](http://www.google.com) into your web browser, the browser sends a request to the DNS server. The DNS server finds the corresponding IP address (like `192.168.1.1` or `74.125.68.102`), and then connects it with the hosting server, allowing the webpage to be displayed on your browser. Without DNS, you would have to type in the numerical IP address directly to access the website.

* ### What is the difference between IP & DNS?
    

The **Domain Name System (DNS)** and **IP addresses** are both crucial components of the internet, but they serve different functions:

* **IP Address**: An IP (Internet Protocol) address is a unique numerical identifier assigned to every device connected to a network. It’s like a phone number for your computer or any device connected to a network. There are two main types of IP addresses: IPv4 (e.g., 192.168.1.1) and IPv6 (e.g., 2001:0db8:85a3:0000:0000:8a2e:0370:7334). Just like how you dial a phone number to call someone, devices use IP addresses to reach each other.
    
* **DNS**: The Domain Name System (DNS) is like your phone’s contact list but for websites. Instead of remembering all the numbers, you just need to know the name. When you want to use Google, you type the domain name ([google.com](http://google.com)) in your web browser, not the numeric IP address of the server hosting Google. The main purpose of DNS is to translate human-friendly domain names like “[google.com](http://google.com)” into the machine-readable IP addresses.
    

In summary, the main difference between IP addresses and DNS is that an IP address is a unique numerical identifier assigned to every device connected to a network, while DNS (Domain Name System) translates human-friendly domain names into IP addresses. DNS and IP addresses work together to connect you to websites. Think of it as using your contact list to dial a friend’s phone number.

---

# DNS Architecture (How does DNS work?)

The Domain Name System (DNS) works in a series of steps:

1. **User Request**: When you type a URL like [`www.example.com`](http://www.example.com) into your web browser, a DNS query is initiated.
    
2. **Contacting ISP DNS Recursor**: The query first reaches the DNS recursor, a server designed to receive queries from client machines. This server can be thought of as a librarian who is asked to find a particular book in a library. For example "JIO, AIRTEL, IDEA", from which your computer is getting an internet connection to connect with the INTERNET.
    
    When your computer connects to the internet through an Internet Service Provider (ISP) like JIO, it typically uses the DNS servers provided by the ISP. These servers act as DNS recursors.
    
    A DNS recursor is a server designed to receive queries from client machines through applications such as web browsers. The recursor is responsible for making additional requests in order to satisfy the client’s DNS query.
    
3. **Querying the Root Nameserver**: The recursor then queries a root nameserver, which can be thought of as an index in a library that points to different racks of books. It serves as a reference to other more specific locations.
    
4. **Accessing the TLD Nameserver**: The next step is to access the Top Level Domain (TLD) nameserver. This server can be thought of as a specific rack of books in a library. For [`www.example.com`](http://www.example.com), the TLD is `.com`.
    
5. **Reaching the Authoritative Nameserver**: Finally, the query reaches the authoritative nameserver, which can be thought of as a dictionary on a rack of books. This server provides the final translation of the domain name into its corresponding IP address. For example GoDaddy, BigRock, Namecheap, and BlueHost etc. are examples of Authoritative Nameservers.
    
6. **Retrieving the IP Address**: The IP address is then returned to the DNS recursor, which in turn sends it back to your computer.
    
7. **Connecting to the Website**: Your computer uses this IP address to connect to the website, and the website content is returned to your browser.
    

This entire process happens behind the scenes and requires no interaction from the user apart from the initial request. It’s a complex but essential system that allows us to navigate the internet using easy-to-remember domain names instead of numerical IP addresses.

![DNS Architecture and How the DNS work actually](https://cdn.hashnode.com/res/hashnode/image/upload/v1705826589834/8d604738-bb37-4352-a0ac-7d1a34e38087.png align="center")

---

# Understanding Recursive and Iterative Queries in DNS Resolution

* **<mark>Recursive Query</mark>**
    

When you enter a URL (like [www.rakamodify.online](http://www.rakamodify.online)) in your web browser, the browser sends a request to the Internet Service Provider’s (ISP) DNS server to resolve the domain name into an IP address. This is known as a **recursive query**. The ISP’s DNS server is responsible for providing a definitive answer, either the IP address or an error message.

* **<mark>Iterative Query</mark>**
    

If the ISP’s DNS server doesn’t know the IP address for the domain, it will perform an **iterative query** to find it. This involves the following steps:

1. The ISP’s DNS server queries a **Root DNS server**. The Root DNS server doesn’t know the IP address, but it knows where to find the DNS server for top-level domains (TLDs) like `.com`, `.online`, `.org`, etc.
    
2. The ISP’s DNS server then queries the **TLD DNS server**. The TLD DNS server doesn’t know the IP address, but it knows where to find the DNS server for the specific domain (like [rakamodify.online](http://rakamodify.online)).
    
3. Finally, the ISP’s DNS server queries the **Authoritative DNS server** (which could be hosted by providers like Namecheap, BigRock, Bluehost, GoDaddy, etc.). The Authoritative DNS server knows the IP address for the specific domain and returns it to the ISP’s DNS server.
    

* **<mark>Non-Recursive Query</mark>**
    

A Non-Recursive query in DNS is a type of query where the DNS resolver already knows the answer. It either immediately returns a DNS record because it already stores it in local cache, or queries a DNS Name Server which is authoritative for the record, meaning it definitely holds the correct IP for that hostname.

This process of the ISP’s DNS server querying the Root DNS server, TLD DNS server, and Authoritative DNS server to find the IP address for a domain is known as an iterative query. The ISP’s DNS server does the “hard work” of finding the IP address, hence the term “recursive resolver”.

Once the IP address is found, the ISP’s DNS server returns it to your web browser, which can then request the webpage from the web server at that IP address.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705828644578/9875c2c0-6a46-4299-b5df-69f90fe0bc7e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705828231918/d5256818-04da-4b43-827b-ecf1ea3ca783.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705829067442/91eb99bf-6d85-4321-9d2c-5167a7436106.png align="center")

---

# How to configure a DNS server?

We’re utilizing a Cloud Service for our setup, which includes two instances. The first instance is a web server, and the second one is a DNS server.

Here’s a brief overview of the configuration:

| AWS Cloud Instance | Private IP | Public IP | Configured For |
| --- | --- | --- | --- |
| WEB-SERVER | 162.25.32.11 | 72.46.86.21 | web |
| DNS-SERVER | 162.25.32.11 | 72.46.25.41 | dns |

Now, let’s dive into the configuration of each instance.

1. ### WB-SERVER (`On your web-server instance`)
    

Follow these article links for web-server setup:

* For Dynamic MySQL + WordPress Setup:-
    

[`https://www.rakamodify.online/deploy-wordpress-mariadb-php-apache-web-server-on-rhel9-with-easy-steps`](https://www.rakamodify.online/deploy-wordpress-mariadb-php-apache-web-server-on-rhel9-with-easy-steps)

* For Dynamic Web Setup on Kubernetes Cluster:-
    

[`https://www.rakamodify.online/session-1`](https://www.rakamodify.online/session-1)

* For a simple static web setup
    

```plaintext
# yum install -y httpd
# firewall-cmd --permaanent-add --port=80/tcp
# firewall-cmd --reload
# systemctl enable --now httpd
# echo "Congratulations! web service is running." > /var/www/html/index.html
# systemctl restart httpd
```

```plaintext
# curl http://localhost
Congratulations! web service is running.
```

---

1. ### DNS-SERVER (`On your dns-server instance`)
    

```plaintext
# yum install -y bind bind-utils
# systemctl enable --now named
# firewall-cmd --permanent-add-port=53/udp
# firewall-cmd --reload
```

* Configuration in `/etc/named.conf`
    

```plaintext
[root@dns ~]# vim /etc/named.conf
options {
        directory "/var/named";
        recursion no;
};
zone "rakamodify.online" IN {
        type master;
        file "test";
};
```

* Entry of DNS targets in `/var/named/test`
    

```plaintext
# cp -p /var/named/named.empty /var/named/test
# vim /var/named/test

$TTL 1M
@       IN SOA  @ rname.invalid. (
                                        0       ; serial
                                        1D      ; refresh
                                        1H      ; retry
                                        1W      ; expire
                                        3H )    ; minimum

rakamodify.online.             IN      NS          ns1.rakamodify.online.
rakamodify.online.             IN      NS          ns2.rakamodify.online.
ns1                            IN      A           72.46.25.41
ns2                            IN      A           72.46.25.41
rakamodify.online.             IN      A           72.46.86.21
photos                         IN      A           72.46.86.21
www                            IN      CNAME       rakamodify.online.
```

* Open your Domain Name registrar account and change the nameserver and child nameserver entry.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705891491826/a65e33d0-9c67-43bc-9f5a-ed2ee6fe8633.png align="center")

* Change nameserver to `custom DNS`
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705891695079/39974441-0ab0-439d-aa7b-9ca0812b5f4a.png align="center")

* And make the following entry:
    

<mark>ns1.rakamodify.online</mark>

<mark>ns2.rakamodify.online</mark>

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705891766401/677a5532-49a5-4b55-a042-329107a3c49e.png align="center")

* Now add the IPv4 address for the newly added namespace for redirection.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705892291361/9b6daa4e-1bb1-4c66-9984-a02c2ccba3bd.png align="center")

Now how this entire setup will work:-

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1705894029248/283d52a4-b894-4512-a0b6-f80dec1c32bf.png align="center")

Wait for some time to update DNS cache with updated configuration. Then check your Domain - IP name resolution with networking command `# nslookup`

Check locally on your DNS Instance Server

```plaintext
# nslookup rakamodify.online localhost
# nslookup www.rakamodify.online localhost
# nslookup www.rakamodify.online 8.8.8.8
# nslookup www.rakamodify.online 8.8.4.4
```

And output should be like this

```plaintext
Server:         localhost
Address:        ::1#53

Name:   rakamodify.online
Address: 72.46.86.21
```

Congratulations