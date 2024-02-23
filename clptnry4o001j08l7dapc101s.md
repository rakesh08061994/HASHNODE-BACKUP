---
title: "Linux Servers: We should know as a DevOps Engineer"
datePublished: Wed Dec 06 2023 11:00:58 GMT+0000 (Coordinated Universal Time)
cuid: clptnry4o001j08l7dapc101s
slug: linux-servers-we-should-know-as-a-devops-engineer
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701867420500/b8c2b19b-2bf9-46e0-b2da-16b3e5363b47.png
tags: cloud, virtual-machine, linux, technology, server, computer-science, beginner, learning, cloud-computing, beginners, containers, containerization, learning-journey, linux-for-beginners, linux-basics

---

### Introduction: ( What are servers ? )

Servers are powerful computers that store, manage, and distribute data or services to other computers, known as clients, over a network. They handle various tasks like hosting websites, storing files, managing emails, and providing access to resources for multiple users or devices. Essentially, servers act as central hubs, responding to requests from clients and delivering the required information or services across a network.

As you step into the dynamic realm of technology during your academic journey, diving into the world of Linux servers might just be the game-changer you're looking for. Picture this: If you're in the middle of your computer science or IT graduation, exploring the endless possibilities of building your tech career. Now, why should Linux servers be on your radar?

In the bustling landscape of the digital age, where everything from streaming movies to global communication relies on the seamless functioning of technology, Linux servers stand tall as the unsung heroes behind the scenes. They're the backbone of nearly everything digital – from your favorite websites and apps to the secure transfer of data worldwide.

Learning about Linux servers isn't just about acing exams or landing a job (though it helps immensely there too!). It's about understanding the heartbeat of modern technology. Imagine being the wizard who ensures that when you tap on Instagram, it loads in a blink, or when you Google something, it magically appears on your screen. That magic? Well, it's all thanks to Linux servers!

Think of them as the secret sauce behind the scenes, ensuring that the apps you love work flawlessly, your data is secure, and the digital world keeps spinning smoothly. As you step into the real world of tech, understanding Linux servers opens doors to a realm where you're not just a user but the master architect of digital experiences. So let's deep dive into the ocean of Linux servers and grasp the overview of servers' needs and importance in the real technology world.

---

### Evolution of Servers:

The evolution of server deployment has followed a progression from local, on-premises solutions to cloud-based and containerized environments from time to time.

1. **Local Servers:** At the start, computers used as servers were kept right where they were needed—in the same place as the people using them. Think of it like having a computer in your room that only you and your roommates can use.
    
2. **On-Premises Servers:** As things got bigger, organizations set up their own special rooms (data centers) filled with servers. It's like having a big library on campus—everyone from the university can use it, and the library staff takes care of all the books (data) and facilities (hardware).
    
3. **Virtual Machines (VMs):** Imagine having a single supercomputer that can act like many smaller computers. That's what happened with virtual machines. It's like having a giant pizza that you can cut into smaller slices—each slice is a separate server doing its own thing, but they're all from the same big pizza.
    
4. **Cloud Servers:** Now, picture this: instead of owning your own library, you can borrow books from a huge library online whenever you need them. Cloud servers are like that—they're not in your place, but you can use them whenever and however you want through the internet.
    
5. **Containers:** Containers are like super-light, portable boxes. They hold just the right amount of stuff (applications) and can be moved around easily. It's like having small, ready-to-use toolkits that you can carry and use anywhere you need.
    

---

### How Server work? (A simple example)

1. **Receiving Requests:** Servers are like smart assistants at a huge tech office. They're always ready to take requests from computers, phones, or any devices that need information or services.
    
2. **Figuring Out What's Needed:** When a request comes in, it's like a task landing on the assistant's desk. The server reads it and understands what's being asked, just like the assistant understands the task given to them.
    
3. **Getting the Job Done:** The server then acts! It either finds the needed information from its big digital archive or does a specific task, like showing a website, sending a file, or handling data.
    
4. **Returning the Result:** Just like the assistant completes the task and brings back the result, the server sends back what was requested. It ensures you get the website, and the file you're downloading or confirms your data has been stored correctly.
    
5. **Handling Many Tasks:** Imagine the assistant handling lots of tasks from different colleagues at once. Similarly, servers manage multiple requests from different devices simultaneously, ensuring everyone gets what they need.
    

---

### Types of Servers by Purpose:

1. **DNS (Domain Name System):**
    
    * **Introduction:** DNS translates domain names to IP addresses, enabling users to access websites using human-readable names.
        
    * **Importance for a Company:** Critical for network functionality and online presence. Ensures reliable and efficient web browsing, email delivery, and other internet services.
        
    * **Real-world Scenario:** When you type a website's name (like [www.example.com](http://www.example.com/)) into a browser, DNS translates it to an IP address (like 192.0.2.1) to connect you to the site.
        
2. **Apache & Nginx:**
    
    * **Introduction:** Both are web servers; Apache is known for its flexibility and Nginx for its high performance and scalability.
        
    * **Importance for a Company:** Serve web content efficiently, handle HTTP requests, and host websites or web applications.
        
    * **Real-world Scenario:** Websites like WordPress and Drupal often use Apache or Nginx to deliver web pages to users.
        
3. **Reverse Proxy & Load Balancer:**
    
    * **Introduction:** Reverse proxy forwards client requests to servers and load balancer distributes incoming network traffic across multiple servers.
        
    * **Importance for a Company:** Improve performance, security, and scalability by managing traffic efficiently and balancing server loads.
        
    * **Real-world Scenario:** Companies like Netflix use load balancers to distribute user requests across multiple servers, ensuring uninterrupted streaming.
        
4. **Tomcat Apache:**
    
    * **Introduction:** Tomcat is an application server primarily used to deploy Java servlets and JSPs.
        
    * **Importance for a Company:** Host Java-based web applications and support their execution.
        
    * **Real-world Scenario:** Banking applications that use Java-based technologies might be hosted on Tomcat servers.
        
5. **NFS (Network File System) & Samba:**
    
    * **Introduction:** NFS allows file sharing between systems in a network, while Samba enables file and print services for SMB/CIFS clients.
        
    * **Importance for a Company:** Facilitates seamless file sharing and access across heterogeneous systems (Windows, Linux, etc.).
        
    * **Real-world Scenario:** In an office setting, employees can access shared files stored on a central server using NFS or Samba.
        
6. **MariaDB, PostgreSQL, MongoDB:**
    
    * **Introduction:** These are different types of databases used for storing and managing data.
        
    * **Importance for a Company:** Store, retrieve, and manipulate data efficiently for various applications.
        
    * **Real-world Scenario:** A social media platform might use MongoDB to manage vast amounts of unstructured data, while financial institutions might prefer PostgreSQL for its reliability and ACID compliance.
        
7. **Mail Server, FTP, DHCP:**
    
    * **Introduction:** Mail servers handle email transmission, FTP servers manage file transfers, and DHCP assigns IP addresses to devices.
        
    * **Importance for a Company:** Facilitate email communication, file sharing, and automatic IP allocation within the network.
        
    * **Real-world Scenario:** A company's internal network might use DHCP to assign IP addresses to devices, an FTP server to share files internally, and a mail server for intra- and inter-organizational communication.
        

---

So In our upcoming articles, we'll explore individual Linux servers in detail. Stay connected, let's learn together, and leverage our knowledge with the right intention to serve society with high potential.