## OWASP Top 10, Pentesting and/or Web Applications

### [1. Differentiate XSS from CSRF.]()

XSS, or Cross-Site Scripting, is a type of security vulnerability where an attacker injects malicious scripts into a trusted website. When users visit the compromised page, the malicious scripts run in their browsers. These scripts can steal user data, like cookies and session tokens, or redirect users to harmful sites. XSS exploits the trust users have in a specific website.

CSRF, or Cross-Site Request Forgery, is another security vulnerability where an attacker tricks a user into performing actions they did not intend to do on a different site where they are authenticated. This happens when the user is logged into a website, and the attacker sends a request to that site using the user's credentials without their knowledge. For example, an attacker could make the user unknowingly transfer money or change account details. CSRF exploits the trust a website has in the user's browser.

The main difference is that XSS attacks involve injecting and executing malicious scripts, usually affecting the user's browser and data. In contrast, CSRF attacks trick users into performing actions they didn't intend on websites where they are authenticated, without injecting code. Both are serious threats and require different approaches to prevent, such as using input validation for XSS and tokens for CSRF.

### [2. What do you do if a user brings you a pc that is acting 'weird'? You suspect malware.]()

First, ask the user about the specific problems they are experiencing and any recent changes they made, like installing new software or opening suspicious emails. This information can give clues about the source of the problem.

Next, disconnect the PC from the internet to prevent any potential malware from spreading or communicating with external servers. This helps contain any malicious activity.

Then, boot the computer into Safe Mode. Safe Mode loads only essential system files, which can help when trying to remove malware. In Safe Mode, run a full scan with an updated antivirus or anti-malware tool to detect and remove any threats.

Check the startup programs and processes running on the PC. Look for anything unusual or unfamiliar that could be malware. You can use tools like Task Manager or Autoruns to help identify suspicious programs.

If the antivirus finds malware, follow its instructions to remove it. After removal, run additional scans to ensure the system is clean. If malware is still present, consider using a bootable antivirus rescue disk to scan and remove threats outside of the operating system.

Once the system is clean, update all software and the operating system to patch any vulnerabilities. Advise the user on safe computing practices, like not opening unknown emails or downloading software from untrusted sources, to help prevent future infections.

Finally, make sure to back up important data regularly. If malware causes significant damage, having backups can help restore lost files and get the system back to normal quickly.

### [3. What is the difference between tcp dump and FWmonitor?]()

TCPdump and FWmonitor are tools used to capture network traffic, but they serve different purposes and are used in different contexts.

TCPdump is a command-line packet analyzer tool used to capture and display network traffic passing through a network interface. It is widely used for network troubleshooting and analysis. With TCPdump, you can see all packets that pass through an interface, allowing you to analyze data flows, identify issues, and monitor network activity. It's a versatile tool that works on various operating systems and provides detailed information about each packet, such as source and destination addresses, protocols, and more.

FWmonitor, on the other hand, is a specific tool used in Check Point firewall environments. It is used to capture traffic at different stages as it passes through the Check Point firewall. FWmonitor provides a view of packets at multiple points in the firewall processing chain, helping troubleshoot issues related to firewall rules and packet handling. It shows how packets are processed by the firewall, from the initial arrival to the final routing or blocking decision, giving insight into how traffic is managed by the firewall.

In summary, TCPdump is a general-purpose tool for capturing network packets on any system, while FWmonitor is specialized for capturing traffic within Check Point firewalls, focusing on how packets are handled at different stages. Both tools are useful for network analysis but are used in different scenarios.

### [4. Do you know what XXE is?]()

XXE stands for XML External Entity, which is a security vulnerability found in applications that process XML input. This vulnerability occurs when an XML parser allows the processing of external entities. An attacker can exploit this by crafting malicious XML data that includes external entity references, which can then access files on the server, interact with internal systems, or even execute harmful code.

For example, if an application parses XML data from untrusted sources and does not disable external entities, an attacker can manipulate the XML to include a reference to a file on the server, such as `/etc/passwd`, and retrieve its contents. This can lead to sensitive data exposure or unauthorized access to the system.

To prevent XXE attacks, it's important to configure XML parsers to disable the processing of external entities. This involves setting secure configurations and using libraries or frameworks that do not process external entities by default. It's also a good practice to validate and sanitize XML input to ensure it comes from trusted sources. By taking these steps, you can protect your applications from XXE vulnerabilities.

### [5. Explain man-in-the-middle attacks.]()

A man-in-the-middle (MITM) attack is when an attacker secretly intercepts and relays messages between two parties who believe they are directly communicating with each other. The attacker can listen to, modify, or inject messages into the communication without either party knowing.

This type of attack often happens on unsecured or poorly secured networks, like public Wi-Fi. An attacker can position themselves between a user and the network, capturing data such as login credentials, credit card numbers, or personal information as it is transmitted.

There are several methods attackers use to perform MITM attacks. One common method is ARP spoofing, where the attacker sends false ARP (Address Resolution Protocol) messages to associate their MAC address with the IP address of a legitimate server. This tricks the user's device into sending data to the attacker instead of the intended recipient.

To protect against MITM attacks, use secure connections like HTTPS and ensure websites use SSL/TLS certificates. Avoid using public Wi-Fi for sensitive transactions, and use VPNs to encrypt your internet traffic. Additionally, keeping your software and systems updated with the latest security patches helps protect against vulnerabilities that could be exploited in MITM attacks.

### [6. What is a Server Side Request Forgery attack?]()

Server Side Request Forgery (SSRF) is a type of security vulnerability where an attacker tricks a server into making unauthorized requests to internal or external resources. This happens when an application takes user input to create a request and fetches data without properly validating the input.

In an SSRF attack, the attacker can make the server send requests to other services or systems that it has access to, which might not be directly accessible by the attacker. For example, if a web application fetches content from a URL specified by the user, an attacker can manipulate this URL to make the server request internal services or sensitive endpoints, like metadata services in cloud environments.

This type of attack can lead to exposure of sensitive information, such as internal network details, server configuration, or even unauthorized access to other services. The server might also interact with malicious resources controlled by the attacker.

To prevent SSRF attacks, it's important to validate and sanitize all user inputs, especially when they are used to make requests. Restrict the server’s network access to only what is necessary and use allowlists for URLs that the server can access. Regularly update and patch server software to mitigate vulnerabilities that could be exploited through SSRF attacks.

### [7. Describe what are egghunters and their use in exploit development.]()

Egghunters are a technique used in exploit development to locate specific code or payload in memory. When exploiting a vulnerability, especially in situations where the space for shellcode is limited, egghunters help find and execute a larger payload that is stored elsewhere in memory.

In simple terms, an egghunter is a small piece of code that searches through memory for a specific pattern, known as the "egg." The egg is a unique marker that is placed at the beginning of the actual payload. Once the egghunter finds this marker, it knows that the payload follows and jumps to execute it.

This technique is useful in scenarios where you can't place your entire payload directly into the buffer being exploited. Instead, you inject the egghunter in the vulnerable buffer and place the larger payload elsewhere, such as in an environment variable or another part of the memory.

By using egghunters, attackers can bypass constraints on buffer size and execute complex payloads that wouldn't fit directly into the overflowed buffer. This makes them a powerful tool in advanced exploit development, allowing attackers to execute their code under challenging conditions.

### [8. How is pad lock icon in browser generated?]()

The padlock icon in a browser appears when you visit a website that uses HTTPS, indicating a secure connection. This icon is generated when the website's server and your browser establish an encrypted connection using SSL/TLS protocols.

When you type a website address and hit enter, your browser sends a request to the server. If the server is configured to use HTTPS, it sends back a digital certificate, which contains a public key and is issued by a trusted Certificate Authority (CA). 

Your browser checks the certificate to ensure it is valid and has not expired. If everything checks out, your browser and the server perform a handshake process to establish an encrypted connection. This encryption ensures that data sent between your browser and the server is secure and cannot be easily intercepted.

Once the secure connection is established, the browser displays the padlock icon to let you know the website is secure. This icon helps you verify that your connection to the website is private and protected from eavesdropping or tampering. If the padlock icon is missing or shows a warning, it might mean there is an issue with the website's security certificate or the connection is not fully secure.

### [9. What is Same Origin Policy and CORS?]()

The Same Origin Policy is a security feature implemented by web browsers to prevent websites from interacting with each other unless they share the same origin. The origin is defined by the combination of the protocol (like HTTP or HTTPS), domain, and port. This policy ensures that scripts from one website cannot access data on another website, protecting sensitive information from being stolen or manipulated by malicious scripts.

For example, if you visit a website `https://example.com`, scripts on that site can only interact with resources from `https://example.com`, not from `https://another.com`. This restriction helps prevent attacks like Cross-Site Scripting (XSS) by limiting how data can be shared between different websites.

CORS, or Cross-Origin Resource Sharing, is a mechanism that allows controlled access to resources from different origins. It provides a way for web servers to specify who can access their resources and how. With CORS, a server can send HTTP headers that tell the browser to allow a web application from a different origin to access its resources.

For instance, if a web application hosted on `https://myapp.com` needs to access resources from `https://api.example.com`, the server at `api.example.com` can use CORS headers to grant permission. This is useful for web applications that rely on APIs hosted on different domains, enabling them to function correctly while maintaining security.

Together, the Same Origin Policy and CORS work to balance security and functionality on the web, ensuring that resources are protected while allowing necessary cross-origin interactions.
