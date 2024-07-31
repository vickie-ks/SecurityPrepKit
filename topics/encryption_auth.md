## Encryption and Authentication

### [1. What are common ports involving security, what are the risks and mitigations?]()

The common ports involving security are Port 21(FTP), Port 22(SSH), Port 80(HTTP), Port 443 (HTTPS), Port 53(DNS), Port 25(SMTP).

FTP is used for transferring files but sends data in plain text, which can be easily intercepted. To make it secure, it's better to use FTPS or SFTP. Always have strong passwords and limit access to known IPs. Also, firewalls can help in controlling who gets in and out.

SSH is essential for remote access but often targeted by hackers trying different passwords. Use strong, unique passwords or better yet, SSH keys. Changing the default port number can confuse attackers. Adding tools like fail2ban to block repeated failed attempts and disabling root login can also help.

HTTP is used for website traffic but isn't secure as it sends data in plain text. Using HTTPS instead encrypts the data. Regularly updating the web server software, using web application firewalls, and conducting security audits can help protect against attacks like XSS and SQL injection.

HTTPS ensures secure web communication but can have vulnerabilities like SSL/TLS flaws. Using strong SSL/TLS configurations, updating SSL/TLS libraries, and employing certificate pinning are good practices. Tools like Qualys SSL Labs can test your SSL/TLS setup.

DNS is like the phonebook of the internet but can be attacked with methods like DNS amplification and cache poisoning. Implementing DNSSEC helps secure DNS queries. Rate limiting can control the number of queries, and keeping DNS software updated is crucial to avoid vulnerabilities.

SMTP is crucial for sending emails but can be misused for spam and spoofing. Implementing SPF, DKIM, and DMARC can help verify emails and prevent misuse. Avoid open relay settings and use TLS to encrypt email data during transmission.

### [2. Which one for DNS?]()

DNS, which acts like the internet's phonebook, can be targeted in several ways. Attackers can perform DNS amplification attacks to overload systems or poison the DNS cache to redirect users to malicious sites. Implementing DNSSEC (Domain Name System Security Extensions) can secure DNS queries and responses, making it harder for attackers to tamper with them. It's also good to use rate limiting to control the number of DNS queries your server processes, and always keep your DNS software up to date to protect against known vulnerabilities. Monitoring DNS traffic for unusual patterns can help detect and mitigate potential threats early.

### [3. Describe HTTPs and how it is used.]()

HTTPS is used to keep your data safe when you browse websites. When you visit a website with HTTPS, the data you send and receive is encrypted. This means that personal information like passwords and payment details are protected from hackers.

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



<link rel="stylesheet" type="text/css" href="{{ "/assets/css/dark-mode-override.css?v=" | append: site.github.build_revision | relative_url }}">