## Encryption and Authentication

### [1. What is a three-way handshake?]()

A three-way handshake is a process used in the TCP/IP network protocol to establish a reliable connection between a client and a server. This process ensures that both parties are ready to communicate and that the connection is synchronized before data is sent.

First, the client sends a SYN (synchronize) message to the server. This message is like a request to start a conversation and includes a random sequence number that will be used to keep track of the data being sent.

The server responds with a SYN-ACK (synchronize-acknowledge) message. This message acknowledges the client's request and includes its own sequence number. It tells the client that the server is ready to communicate.

Finally, the client sends an ACK (acknowledge) message back to the server. This message confirms that the client has received the server's SYN-ACK message and is ready to start the data exchange.

Once these three steps are completed, the connection is established, and the client and server can begin sending data to each other. The three-way handshake ensures that both parties are synchronized and ready for communication, reducing the risk of errors during data transmission.

### [2. How do cookies work?]()

Cookies are small pieces of data stored on your computer by a web browser when you visit a website. They help websites remember information about your visit, like login details, preferences, and what items you have in your shopping cart.

When you visit a website for the first time, the server sends a cookie to your browser, which stores it on your computer. The next time you visit the same site, your browser sends the cookie back to the server. This helps the server recognize you and load your preferences or keep you logged in.

Cookies can have different purposes. Some cookies are used for session management, allowing you to stay logged in as you navigate through different pages. Others are used to store preferences, like language settings, so the website looks the way you want each time you visit.

Some cookies are used for tracking purposes, helping websites understand how users interact with them. These cookies collect data about your browsing habits, which can be used to show personalized ads or improve website functionality.

While cookies can be helpful, they also raise privacy concerns. Many browsers allow you to manage cookie settings, giving you control over which cookies are stored and how long they remain on your computer. It's a good practice to review and clear cookies regularly to maintain your privacy and ensure optimal browser performance.

### [3. How do sessions work?]()

Sessions are a way for websites to remember information about a user across multiple pages or visits. When you log into a website or start a new interaction, the server creates a session for you. This session stores data like your login status or items in your shopping cart.

When you first connect to a website, the server assigns you a unique session ID, which is sent to your browser as a cookie or included in the URL. This session ID acts like a key, allowing the server to retrieve your session data whenever you request a new page.

As you navigate through the website, your browser sends the session ID with each request. The server uses this ID to access your session data and keep track of your activity. This way, you can move between pages without losing your login status or other important information.

Sessions usually last until you log out or close your browser. They can also expire after a certain period of inactivity for security reasons. This helps protect your account by automatically logging you out if you forget to do so.

Sessions are essential for creating smooth and personalized user experiences on the web. They allow websites to maintain state and provide consistent services without needing you to re-enter information repeatedly.

### [4. Explain how OAuth works.]()

OAuth is a protocol that allows you to give websites or applications permission to access your information on another service without sharing your password. It is commonly used for logging into a website using your Google, Facebook, or Twitter account.

When you want to use OAuth to log in to a website, the website redirects you to the service you want to use, like Google. You log in to Google, and it asks if you want to give the website permission to access your information, like your email address.

If you agree, Google sends back a special code to the website. This code is a temporary token that the website can use to access your information. The website exchanges this token for a more secure access token, which it can use to make requests on your behalf.

With this access token, the website can access the information you allowed, such as your profile details, without knowing your actual password. This way, you stay secure because you don’t have to share your password with every website or app you use.

OAuth makes it easier to use different services together and keeps your accounts secure by letting you control what information is shared and revoke access when you want. It’s a safe way to allow limited access to your data across multiple platforms.

### [5. Explain how JWT works.]()

JWT, or JSON Web Token, is a way to securely transmit information between parties as a JSON object. It is often used for authentication and information exchange in web applications.

When you log into a website, the server creates a JWT and sends it back to your browser. This token contains a header, a payload, and a signature. The header specifies the type of token and the algorithm used for signing. The payload contains the claims, which are statements about the user, like their ID and roles.

The server signs the JWT using a secret key, creating the signature. This ensures that the token hasn’t been altered. When your browser makes requests to the server, it includes the JWT in the headers. The server verifies the signature using the secret key to ensure the token is valid.

JWTs are self-contained, meaning they carry all the information needed for authentication. This makes them efficient, as the server doesn’t need to store session data. However, because JWTs can be large, they should be used carefully to avoid performance issues.

JWTs can be used for stateless authentication, allowing users to stay logged in without storing session data on the server. This makes JWTs ideal for scalable applications and APIs, where maintaining server-side sessions can be challenging.

### [6. What is a public key infrastructure flow and how would I diagram it?]()

A Public Key Infrastructure (PKI) is a system that helps manage and secure digital certificates and public-private key pairs used for encryption and authentication. It ensures secure communication and verifies the identity of users and devices in a network.

In PKI, a Certificate Authority (CA) is a trusted entity that issues digital certificates. These certificates associate a public key with a particular identity, like a person or organization. When you want to communicate securely, you request a certificate from the CA. The CA verifies your identity and issues a certificate that includes your public key.

When someone wants to send you encrypted data, they use your public key from the certificate to encrypt it. Only you can decrypt this data using your private key, which is kept secret. This process ensures that the communication is secure and that the data comes from a verified source.

To diagram a PKI flow, you would start with the user or device requesting a certificate from the CA. Then, show the CA verifying the identity and issuing the certificate. Next, depict the distribution of the public key to other users or systems. Finally, illustrate how encrypted communication occurs using the public and private keys.

This flow helps visualize how PKI enables secure communication and trust within a network by ensuring that public keys are associated with verified identities and that only the intended recipient can decrypt the data.

### [7. Describe SSL handshake.]()

The SSL handshake is a process that establishes a secure connection between a client and a server over the internet. It ensures that data exchanged between them is encrypted and secure.

When you connect to a website using HTTPS, your browser (the client) starts the SSL handshake by sending a "ClientHello" message to the server. This message includes the SSL/TLS version and a list of supported encryption algorithms.

The server responds with a "ServerHello" message. It chooses the encryption algorithm to use and sends its digital certificate, which contains its public key, to the client. This certificate is issued by a trusted Certificate Authority (CA) and helps verify the server's identity.

The client verifies the server's certificate to ensure it is valid and trusted. If everything checks out, the client generates a session key, encrypts it with the server's public key, and sends it back to the server. Only the server can decrypt this session key using its private key.

Once the server decrypts the session key, both the client and server use it to encrypt and decrypt the data they exchange. This symmetric encryption ensures the communication remains private and secure throughout the session.

The SSL handshake is crucial for establishing a secure, encrypted connection, allowing users to communicate with websites safely, protecting sensitive information like passwords and credit card numbers.

### [8. How does HMAC work?]()

HMAC, or Hash-based Message Authentication Code, is a method used to verify the integrity and authenticity of a message. It uses a cryptographic hash function along with a secret key to create a unique code for a message.

When you send a message, HMAC combines the message with a secret key and passes it through a hash function like SHA-256. This process generates a fixed-size code known as a hash value or HMAC code. The sender includes this HMAC code with the message.

The receiver, who also has the secret key, performs the same process: combining the received message with the secret key and hashing it. If the generated HMAC code matches the one sent with the message, it means the message is authentic and hasn’t been tampered with.

HMAC ensures that even if someone intercepts the message, they cannot alter it or create a new valid HMAC code without the secret key. This makes HMAC useful for ensuring data integrity and authenticity in secure communications, especially when transferring sensitive information.

### [9. Why HMAC is designed in that way?]()

HMAC is designed to ensure both data integrity and authenticity, making it a strong tool for secure communication. It combines a cryptographic hash function with a secret key to produce a hash value that acts as a fingerprint for the data. This design helps in confirming that the data hasn't been changed and is from a legitimate source.

The reason HMAC uses a secret key along with the hash function is to prevent attackers from being able to create a valid hash on their own. Without the key, even if an attacker knows the hash function used, they cannot generate a valid HMAC for altered or fake data. This ensures that only someone with the correct key can verify or generate the HMAC.

The process of hashing the data twice with the key, once before and once after, adds another layer of security. This double hashing method helps protect against certain types of cryptographic attacks that might be able to exploit weaknesses in the hash function.

Overall, HMAC’s design focuses on security, making it robust against tampering and unauthorized modifications. It’s used widely in network protocols and applications where secure data transfer is crucial.

### [10. What is the difference between authentication vs authorization name spaces?]()

Authentication and authorization are two key concepts in security, and they serve different purposes.

Authentication is about verifying who you are. It's like showing your ID card to prove your identity. In the digital world, this usually involves entering a username and password, scanning a fingerprint, or using a face ID to log into a system or application. The system checks if your credentials match what's on record, confirming your identity.

Authorization, on the other hand, is about what you can do once your identity is confirmed. After you've logged in, authorization determines what resources you have access to and what actions you can perform. For example, a user might be able to view their profile but not edit other users' profiles. Authorization ensures that you only have access to the resources and actions that you are allowed.

In summary, authentication is the process of verifying your identity, while authorization is about granting you permission to access certain resources or perform specific actions based on your verified identity. Both are important for maintaining security and ensuring that only authorized users can perform sensitive operations.

### [11. What’s the difference between Diffie-Hellman and RSA?]()

Diffie-Hellman and RSA are both cryptographic algorithms used to secure data, but they work in different ways and are used for different purposes.

Diffie-Hellman is mainly used for secure key exchange. It allows two parties to create a shared secret over an insecure channel without actually sending the secret itself. Each party generates a public and a private key, exchanges the public keys, and uses them to compute the shared secret. This secret can then be used to encrypt and decrypt messages between the parties. Diffie-Hellman is not used for encryption directly but is crucial for establishing a secure channel.

RSA, on the other hand, is used for both encryption and digital signatures. It relies on the mathematical difficulty of factoring large prime numbers. In RSA, a user generates a pair of keys: a public key for encrypting messages and a private key for decrypting them. The public key can be shared openly, while the private key must be kept secret. RSA can also be used to verify the authenticity of a message through digital signatures, ensuring that the message comes from the claimed sender.

In summary, Diffie-Hellman is focused on securely exchanging keys, while RSA is versatile, providing encryption, decryption, and digital signatures. Both are essential for secure communications but serve different roles in cryptographic protocols.

### [12. How does Kerberos work?]()

Kerberos is a network authentication protocol used to verify the identity of users and services. It uses a system of tickets and secret keys to allow secure communication over a network, without sending passwords.

When you log into a system using Kerberos, your computer sends a request to the Key Distribution Center (KDC). The KDC has two parts: the Authentication Server (AS) and the Ticket Granting Server (TGS). First, the AS verifies your identity using your password. If everything is correct, it sends back a Ticket Granting Ticket (TGT) encrypted with your secret key.

This TGT acts like a temporary pass that allows you to request access to other services. When you want to access a particular service, your computer sends the TGT to the TGS, asking for a service ticket for that specific service. The TGS verifies the TGT and sends back a service ticket.

Finally, you use this service ticket to authenticate with the desired service, like accessing files or printing documents. The service checks the ticket, and if it’s valid, it allows you access without needing your password again.

Kerberos helps in keeping passwords safe by not sending them over the network and by using temporary tickets that are only valid for a short period. This way, it provides secure and efficient authentication for users and services in a networked environment.

### [13. If you're going to compress and encrypt a file, which do you do first and why?]()

When you want to compress and encrypt a file, it is usually better to compress the file first and then encrypt it. This approach is more efficient and provides better security.

Compressing the file first reduces its size, which means there is less data to encrypt. This can save time and resources during the encryption process. Compression works by finding patterns and redundancies in the data, making it smaller, but encryption turns the data into a random format that doesn't compress well.

Encrypting after compression ensures that the entire content is securely protected. If you encrypt first and then compress, the compression will not work effectively because encrypted data looks random and doesn’t have patterns for the compression algorithm to work with.

By compressing first and then encrypting, you ensure that you save space and processing time while keeping your data securely encrypted. This order maintains the integrity and confidentiality of the data.

### [14. How do I authenticate you and know you sent the message?]()

To authenticate a message from someone and ensure it truly came from them, you can use digital signatures. A digital signature works like a virtual fingerprint, confirming the identity of the sender and ensuring the message hasn’t been tampered with.

The sender uses their private key to create a digital signature for the message. This signature is a unique hash that is generated from the message content. When you receive the message, you use the sender's public key to verify the signature. If the signature matches the message, you can be confident that the message is authentic and hasn't been changed.

This process relies on a pair of keys: a private key, which is kept secret by the sender, and a public key, which is shared openly. As long as the private key is secure, only the sender can create a valid signature for their messages, providing assurance that the message is genuinely from them.

### [15. Should you encrypt all data at rest?]()

Encrypting all data at rest is a good security practice because it protects sensitive information from unauthorized access. If someone gains physical access to your storage devices, encryption ensures they cannot read the data without the decryption key.

However, not all data may need the same level of protection. Critical and sensitive data, like personal information, financial records, or proprietary business data, should definitely be encrypted. For less sensitive data, the decision to encrypt can depend on your security needs and regulatory requirements.

Encrypting all data adds an extra layer of security, but it also requires managing encryption keys properly. If keys are lost or mishandled, data can become inaccessible. Therefore, while encrypting all data at rest enhances security, it’s important to balance it with effective key management and assess the specific needs of your data protection strategy.

### [16. What is Perfect Forward Secrecy?]()

Perfect Forward Secrecy (PFS) is a security feature in encryption protocols that ensures the privacy of past communications, even if the server's private key is compromised in the future. It does this by using temporary session keys for each communication session.

With PFS, every session between a client and a server generates a new set of encryption keys. These keys are used only for that session and then discarded. This means that even if an attacker manages to steal the server’s private key, they cannot decrypt past conversations because each session used a unique key that no longer exists.

PFS is important because it protects your data from being exposed if a future breach occurs. It ensures that only the current session is secure and prevents the possibility of decrypting historical data with stolen keys. Implementing PFS makes it much harder for attackers to access confidential information and strengthens the overall security of communication systems.

### [17. Describe the difference between synchronous and asynchronous encryption.]()


<div class="border-gray-light border-top footer mt-5 pt-3 text-gray text-right">
    <em class="float-right text-gray-light">This site is open source.</em>
</div>
<link rel="stylesheet" type="text/css" href="{{ "/assets/css/dark-mode-override.css?v=" | append: site.github.build_revision | relative_url }}">