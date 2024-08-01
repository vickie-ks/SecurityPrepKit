## Network Level and Logging

### [1. What are common ports involving security, what are the risks and mitigations?]()

The common ports involving security are Port 21(FTP), Port 22(SSH), Port 80(HTTP), Port 443 (HTTPS), Port 53(DNS), Port 25(SMTP).

FTP is used for transferring files but sends data in plain text, which can be easily intercepted. To make it secure, it's better to use FTPS or SFTP. Always have strong passwords and limit access to known IPs. Also, firewalls can help in controlling who gets in and out.

SSH is essential for remote access but often targeted by hackers trying different passwords. Use strong, unique passwords or better yet, SSH keys. Changing the default port number can confuse attackers. Adding tools like fail2ban to block repeated failed attempts and disabling root login can also help.

HTTP is used for website traffic but isn't secure as it sends data in plain text. Using HTTPS instead encrypts the data. Regularly updating the web server software, using web application firewalls, and conducting security audits can help protect against attacks like XSS and SQL injection.

HTTPS ensures secure web communication but can have vulnerabilities like SSL/TLS flaws. Using strong SSL/TLS configurations, updating SSL/TLS libraries, and employing certificate pinning are good practices. Tools like Qualys SSL Labs can test your SSL/TLS setup.

DNS is like the phonebook of the internet but can be attacked with methods like DNS amplification and cache poisoning. Implementing DNSSEC helps secure DNS queries. Rate limiting can control the number of queries, and keeping DNS software updated is crucial to avoid vulnerabilities.

SMTP is crucial for sending emails but can be misused for spam and spoofing. Implementing SPF, DKIM, and DMARC can help verify emails and prevent misuse. Avoid open relay settings and use TLS to encrypt email data during transmission.

### [2. Which one for DNS?]()

DNS (Port 53), which acts like the internet's phonebook, can be targeted in several ways. Attackers can perform DNS amplification attacks to overload systems or poison the DNS cache to redirect users to malicious sites. Implementing DNSSEC (Domain Name System Security Extensions) can secure DNS queries and responses, making it harder for attackers to tamper with them. It's also good to use rate limiting to control the number of DNS queries your server processes, and always keep your DNS software up to date to protect against known vulnerabilities. Monitoring DNS traffic for unusual patterns can help detect and mitigate potential threats early.

### [3. Describe HTTPs and how it is used.]()

HTTPS (Port 443) is used to keep your data safe when you browse websites. When you visit a website with HTTPS, the data you send and receive is encrypted. This means that personal information like passwords and payment details are protected from hackers.

When you connect to an HTTPS website, your browser first talks to the web server and asks for a secure session. The server then sends back its SSL/TLS certificate. This certificate has the server's public key and is signed by a trusted Certificate Authority (CA). Your browser checks the certificate to make sure it is from a trusted source and has not expired.

After verifying the certificate, your browser creates a session key and encrypts it using the server's public key. This encrypted session key is sent to the server. The server then decrypts the session key using its private key. Now, both your browser and the server have the same session key.

Using this session key, all data exchanged between your browser and the server is encrypted. This means even if someone intercepts the data, they cannot read it without the session key. This way, HTTPS ensures that your browsing is secure and your data remains private.

### [4. What is the difference between HTTPS and SSL?]()

**HTTPS (Hypertext Transfer Protocol Secure)** is a protocol used for secure communication over the internet. It is an extension of HTTP, adding a layer of security by encrypting the data exchanged between a user's browser and a web server. HTTPS ensures that the data transmitted is confidential and protected from eavesdroppers and tampering.

**SSL (Secure Sockets Layer)**, on the other hand, is a security technology that establishes an encrypted link between a web server and a browser. SSL is used to secure the data being transmitted over HTTPS. Although SSL is often used interchangeably with TLS (Transport Layer Security), it is actually the predecessor of TLS. Modern HTTPS connections typically use TLS instead of SSL, but the term SSL is still commonly used.

In summary, HTTPS is a protocol for secure communication, while SSL/TLS is the technology used to encrypt the data transmitted over HTTPS.

### [5. How does threat modeling work?]()

Threat modeling is a way to find and fix security problems in a system. First, you need to know what important things you need to protect, like sensitive data or key services.

Next, make a detailed map of your system. This map should show all parts of the system, how data moves, and where people can enter the system. This helps in understanding how everything is connected.

Then, look for possible threats. Think about different ways someone might try to attack the system. Use methods like STRIDE to consider different types of threats, like spoofing or tampering.

After finding threats, look for weak spots in the system that could be attacked. This could be old software that needs updates or bad security settings. Tools and tests can help find these weaknesses.

For each threat and weak spot, think of ways to protect the system. This might mean updating software, fixing settings, or adding security controls. Focus on the most serious risks first.

Check the threat model with other people to make sure it is correct. Talk with developers, security experts, and business people to get their input.

Finally, put the protections in place and keep an eye on the system. Threat modeling is not just done once; you should do it again if the system changes or new threats appear. This way, you can keep the system safe over time.

### [6. What is a subnet and how is it useful in security?]()

A subnet, short for subnetwork, is a smaller network within a larger network. It divides a large network into smaller, more manageable segments. Each subnet has its own range of IP addresses and can communicate with other subnets within the larger network.

Subnets are useful in security for several reasons. First, they help control and limit network traffic. By segmenting the network, you can reduce congestion and improve performance. Each subnet can have specific security policies and controls, making it easier to manage and secure different parts of the network.

Second, subnets can isolate sensitive data and resources. By placing sensitive systems in their own subnet, you limit access to only those who need it. This isolation helps protect against unauthorized access and can contain potential security breaches.

Third, subnets simplify monitoring and managing network security. With smaller segments, it is easier to detect and respond to suspicious activity. Network administrators can set up firewalls and access control lists (ACLs) specific to each subnet, enhancing security.

Finally, subnets can improve fault tolerance and resilience. If one subnet is compromised or experiences an issue, the rest of the network can continue to function normally. This separation helps maintain overall network stability and security. 

In summary, subnets make networks more manageable, improve performance, enhance security, and provide better isolation and control over different parts of the network.

### [7. What is subnet mask?]()

A subnet mask is a number used in networking to divide an IP address into two parts: the network part and the host part. This helps in organizing and managing networks better. 

For example, if you have an IP address like `192.168.1.10` and a subnet mask of `255.255.255.0`, the subnet mask tells the devices that `192.168.1` is the network part, and `10` is the host part. This way, all devices with IP addresses starting with `192.168.1` are in the same network.

The subnet mask is written in the same format as IP addresses, using four numbers separated by dots. Each number can be from 0 to 255. In binary, a subnet mask has a series of 1s followed by a series of 0s. The 1s represent the network part, and the 0s represent the host part.

For example, the subnet mask `255.255.255.0` in binary is `11111111.11111111.11111111.00000000`. This shows that the first three parts of the IP address are the network, and the last part is the host.

Subnet masks are important for defining network boundaries and helping devices communicate correctly. They are used in tasks like assigning IP addresses, routing data, and managing networks. This way, subnet masks help keep networks organized and running smoothly.

### [8. Explain what traceroute is.]()

Traceroute is a tool used to see the path data takes from your computer to a destination on the internet. It helps you understand how data travels and where it might be slowing down or getting stuck.

When you run traceroute, it sends packets to the destination with a starting "Time to Live" (TTL) value of 1. The first router the packet reaches discards it and sends back a message. Traceroute records this and increases the TTL to 2, sending the packet again. This time, it goes to the second router before being discarded, and so on.

By increasing the TTL step by step, traceroute maps out each hop the data makes. It shows the path and the time it takes for each hop. If there's a delay or the path doesn't complete, you can see where the problem might be.

So, traceroute is useful for checking the route and speed of data across the network and helps in finding network issues.

### [9. Explain TCP/IP concepts.]()

TCP/IP is a set of rules that help computers communicate over the internet. It stands for Transmission Control Protocol/Internet Protocol. These rules make sure data can be sent and received between different devices.

First, let’s talk about IP. IP addresses are like home addresses for computers. Each device on a network gets a unique IP address. This address helps to identify where data should go. Just like how a letter needs the right address to reach the correct house, data needs the correct IP address to reach the right device.

TCP is another important part. When you send data over the internet, it gets broken into smaller pieces called packets. TCP helps to manage these packets. It makes sure all packets reach the destination and are put back together in the correct order. If any packets get lost, TCP asks for them again, so nothing is missing.

When you type a website address into your browser, TCP/IP works together to load the page. First, your computer uses IP to find the website’s server. Then, it uses TCP to send your request and receive the web page data in packets.

Think of TCP/IP like a postal system. IP is like writing the address on an envelope, making sure it reaches the correct destination. TCP is like the delivery process, ensuring all parts of the message arrive safely and in order.

This system is reliable and helps different types of devices, like computers, phones, and tablets, to communicate easily over the internet. It’s the backbone of how the internet works, making it possible for us to browse websites, send emails, and stream videos smoothly.

### [10. What is OSI model?]()

The OSI model is a way to understand how different network protocols work together to allow communication between devices. It stands for Open Systems Interconnection and has seven layers, each with a specific function.

The first layer is the Physical layer. It deals with the actual physical connection between devices, like cables and switches. This layer is all about the hardware that sends and receives signals.

Next is the Data Link layer. This layer makes sure that data is transferred correctly between devices on the same network. It handles error detection and correction, making sure the data is sent without mistakes.

The third layer is the Network layer. This layer is responsible for routing data between different networks. It decides the best path for data to travel from one device to another, using IP addresses.

After that comes the Transport layer. This layer ensures that data is transferred reliably and in the right order. It uses protocols like TCP to make sure all data packets reach their destination and are reassembled correctly.

The fifth layer is the Session layer. It manages the connections between devices, establishing, maintaining, and terminating communication sessions. This layer ensures that the connection stays open long enough to transfer all the data.

Then there is the Presentation layer. This layer translates data between the application layer and the network. It converts data into a format that applications can understand and also handles encryption and compression.

Finally, the Application layer. This is the layer closest to the user. It provides network services directly to applications, like web browsers and email programs. This layer makes sure the data is available in a usable form for the end user.

Each layer in the OSI model has a specific role and works with the layers above and below it. This helps in understanding how data moves through a network and makes it easier to troubleshoot problems. The OSI model is a fundamental concept in networking that helps organize and standardize how different network technologies interact.

### [11. How does a router differ from a switch?]()

A router and a switch are both essential devices in networking, but they have different roles. 

A router connects different networks together. It directs data from one network to another. For example, a router connects your home network to the internet. It uses IP addresses to decide where to send data packets. Routers can also offer features like firewall protection, network address translation (NAT), and Wi-Fi connectivity.

A switch, on the other hand, connects devices within the same network. It helps devices like computers, printers, and servers communicate with each other. A switch uses MAC addresses to send data to the correct device. It works within a single network and does not route data between different networks.

Routers are used for routing data between different networks, like between your home network and the internet. Switches are used for switching data between devices in the same network, like between your computer and printer.

In a home setup, you often find a router with built-in switch functions. This device connects to the internet and also connects your devices within the home network. In larger networks, you might find separate routers and switches to manage different tasks more efficiently.

In short, a router connects networks and directs data between them using IP addresses. A switch connects devices within the same network and directs data using MAC addresses. Both are crucial for networking, but they serve different purposes.

### [12. How does a packet travel between two hosts connected in same network?]()

When two hosts are connected in the same network, a packet travels between them in a straightforward way. Let's break down the process step by step.

First, Host A wants to send data to Host B. Host A creates a data packet and includes Host B's IP address as the destination.

Next, Host A needs to find Host B's MAC address. It does this using the Address Resolution Protocol (ARP). Host A sends an ARP request to the network, asking "Who has this IP address?" The request is broadcast to all devices in the network.

Host B receives the ARP request and responds with its MAC address. Now, Host A knows both the IP address and the MAC address of Host B.

Host A then puts the data packet inside an Ethernet frame, adding Host B's MAC address as the destination and its own MAC address as the source.

The Ethernet frame is then sent to the network switch. The switch reads the destination MAC address and knows which port Host B is connected to.

The switch forwards the Ethernet frame to Host B through the correct port. 

Host B receives the Ethernet frame, extracts the data packet, and processes the data. This whole process happens very quickly, allowing seamless communication between the two hosts.

So, in summary, Host A sends an ARP request, gets Host B's MAC address, wraps the data packet in an Ethernet frame, and sends it to the switch, which forwards it to Host B. This is how a packet travels between two hosts in the same network.

### [13. Explain the difference between TCP and UDP.]()

TCP (Transmission Control Protocol) and UDP (User Datagram Protocol) are two core protocols of the Internet Protocol (IP) suite, and they serve different purposes.

TCP is like a reliable delivery service. When you send data using TCP, it makes sure the data arrives correctly and in order. It works by establishing a connection between the sender and receiver before any data is sent. This connection is maintained throughout the communication session. TCP checks for errors and guarantees that lost or damaged packets are resent. Because of these features, TCP is used for applications where accuracy is crucial, like web browsing, email, and file transfers.

UDP, on the other hand, is like sending a message in a bottle. It doesn’t establish a connection before sending data and doesn’t guarantee that the data will arrive. UDP sends packets called datagrams without checking for errors or making sure they are received in the right order. This makes UDP faster but less reliable than TCP. UDP is used for applications where speed is more important than accuracy, such as live streaming, online gaming, and voice over IP (VoIP).

To summarize, TCP is reliable and ensures data is sent and received correctly, making it suitable for applications that need accuracy. UDP is faster but doesn’t guarantee delivery, making it suitable for applications where speed is more important than reliability.

### [14. Which is more secure and why?]()

TCP is generally considered more secure than UDP. Here's why:

TCP has built-in features that enhance security and reliability. One key feature is the three-way handshake process, which establishes a connection between the sender and receiver before any data is transmitted. This handshake helps verify that both parties are ready to communicate and reduces the risk of spoofing and man-in-the-middle attacks.

TCP also has error-checking and correction mechanisms. When data is sent, TCP ensures it arrives correctly by acknowledging receipt of the data. If packets are lost or damaged during transmission, TCP will resend them. This ensures data integrity and reduces the risk of corruption.

In contrast, UDP does not have these security features. Since UDP is connectionless and does not establish a handshake before sending data, it is more susceptible to spoofing and man-in-the-middle attacks. UDP also lacks error-checking and correction, which means there is no guarantee that data will arrive intact or even at all.

For applications requiring secure and reliable data transmission, TCP is the preferred choice. It ensures data is delivered correctly and in order, providing a more secure communication channel. UDP is used for applications where speed is more critical than reliability, but it comes with higher security risks due to its lack of connection management and error-checking.

### [15. What is the TCP three way handshake?]()

The TCP three-way handshake is a process used to establish a connection between a client and a server. It helps both devices confirm they are ready to communicate.

First, the client sends a message called SYN (synchronize) to the server. This message asks if the server is open for a new connection.

Next, the server responds with a SYN-ACK message. This means the server acknowledges the client's request and is also ready to start the connection.

Finally, the client sends an ACK message back to the server. This message confirms that the client received the server's SYN-ACK message.

After these three steps, the connection is established, and data can be sent between the client and the server. This handshake ensures both devices are ready and can communicate properly.

### [16. What is the difference between IPSEC Phase 1 and Phase 2?]()

IPSec is used to secure communications over a network. It has two main phases: Phase 1 and Phase 2.

In Phase 1, the goal is to establish a secure and authenticated channel between two devices, called peers. This phase sets up a secure tunnel for the rest of the communication. The devices use the Internet Key Exchange (IKE) protocol to authenticate each other and agree on the encryption methods they will use. Once they agree and authenticate, they create a secure tunnel, called the IKE Phase 1 tunnel.

In Phase 2, the goal is to negotiate the IPSec security associations (SAs) for the actual data transfer. This phase happens within the secure tunnel established in Phase 1. Here, the devices agree on the parameters for encrypting and securing the actual data packets that will be sent. They create another secure tunnel, called the IPSec Phase 2 tunnel, which is used for the protected data exchange.

So, Phase 1 is about setting up a secure, authenticated channel, while Phase 2 is about agreeing on how to protect the actual data being sent through that channel. Both phases work together to ensure that data is securely transmitted over the network.

### [17. What are biggest AWS security vulnerabilities?]()

One big AWS security vulnerability is misconfigured S3 buckets. When S3 buckets are not set up properly, they can become publicly accessible, allowing anyone on the internet to view or download sensitive data stored in them. This can lead to data breaches and loss of confidential information.

Another common issue is improper use of IAM (Identity and Access Management) permissions. If IAM roles and policies are not correctly configured, it can give users more access than they need. This can lead to unauthorized access to critical resources and data, increasing the risk of malicious activities.

Leaving default security settings unchanged is also a problem. AWS services come with default configurations that might not be secure. Not changing these settings can leave your AWS resources vulnerable to attacks. It's important to customize security settings according to your specific needs.

Using weak or no encryption for data in transit and at rest is another vulnerability. Without proper encryption, data can be intercepted or accessed by unauthorized parties. Ensuring that data is encrypted both while being transmitted and when stored helps protect it from being compromised.

Finally, not keeping AWS environments updated can lead to security vulnerabilities. AWS regularly releases updates and patches to fix known security issues. If these updates are not applied promptly, systems can remain exposed to security threats that have already been addressed.

By addressing these vulnerabilities, you can significantly improve the security of your AWS environment and protect your data from potential threats.


<div class="border-gray-light border-top footer mt-5 pt-3 text-gray text-right">
    <em class="float-right text-gray-light">This site is open source.</em>
</div>
<link rel="stylesheet" type="text/css" href="{{ "/assets/css/dark-mode-override.css?v=" | append: site.github.build_revision | relative_url }}">