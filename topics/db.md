## Databases

### [1. How would you secure a Mongo database?]()

Securing a MongoDB database starts with enabling authentication. By default, MongoDB might not require users to log in, so you should create admin users and enable authentication to ensure only authorized users can access the database.

Next, always use strong passwords for your MongoDB users. Passwords should be complex and hard to guess to prevent unauthorized access. You can also implement role-based access control by assigning specific roles to users, limiting their access to only what they need.

Another important step is to enable encryption. Encrypting data both in transit and at rest protects your data from being intercepted or accessed by unauthorized parties. Use SSL/TLS for encryption during data transmission and enable disk encryption for data at rest.

Make sure to regularly update MongoDB to the latest version. Updates often include security patches that address known vulnerabilities. Keeping your database software up-to-date helps protect it from newly discovered security threats.

Additionally, limit network exposure. Configure your firewall to allow connections only from trusted IP addresses and use Virtual Private Networks (VPNs) to add an extra layer of security. This helps prevent unauthorized users from accessing your MongoDB instance over the internet.

Finally, always back up your data regularly. In case of a security breach or data loss, having recent backups ensures you can restore your database to its previous state without significant data loss. Regular backups are essential for recovery and continuity.

### [2. How would you secure a Postgres database?]()

Securing a Postgres database starts with setting strong authentication methods. You should require users to log in with secure passwords and consider using authentication methods like SCRAM-SHA-256, which provides more security than the default options.

Another important step is to configure user roles and permissions carefully. Assign roles to users based on what they need to do, ensuring they have only the necessary permissions. This limits the risk of unauthorized access to sensitive data.

It's crucial to use SSL encryption for all connections to the database. Enabling SSL ensures that data transmitted between the client and the server is encrypted, protecting it from interception by unauthorized parties.

Regularly updating Postgres to the latest version is also important. Updates often include security patches that fix vulnerabilities. Keeping your database up-to-date helps protect it from potential security threats.

Make sure to configure the Postgres `pg_hba.conf` file properly. This file controls which hosts can connect to the database and how they authenticate. Restrict access to only trusted IP addresses and use secure authentication methods.

Finally, back up your database regularly. Regular backups ensure that you can recover your data in case of a security incident or accidental data loss. Having a reliable backup strategy is crucial for maintaining data integrity and availability.

### [3. Our DB was stolen/exfiltrated. It was secured with one round of sha256 with a static salt.]()
- [What do we do now?]()

    If your database was stolen and it used only one round of SHA-256 with a static salt for securing passwords, there are some important steps you need to take immediately.

    First, inform your users about the breach. Let them know their data might be compromised and advise them to change their passwords, especially if they use the same password on other services. This helps protect them from further damage.

    Next, strengthen your password storage. Instead of using SHA-256 with a static salt, switch to a more secure method like bcrypt or Argon2. These algorithms are designed for password hashing and make it much harder for attackers to crack the passwords.

    Conduct a thorough security audit of your systems to find and fix any vulnerabilities that allowed the breach to happen. Check your network configurations, firewall settings, and access logs to understand how the attackers got in and close those gaps.

    Consider implementing multi-factor authentication (MFA) for added security. This adds another layer of protection even if passwords are compromised, as users will need to provide an additional verification step to access their accounts.

    Finally, review and update your data security policies. Make sure your team follows best practices for securing sensitive data and stays informed about the latest security measures. Regular training and updates are essential for preventing future breaches.

- [Are we at risk?]()

    Yes, you are at risk if your database was secured with only one round of SHA-256 and a static salt. This method is not very strong for protecting passwords because attackers can use techniques like dictionary attacks or brute force attacks to crack them.

    Using a static salt means the same salt is applied to all passwords, making it easier for attackers to precompute hash values and find matches. If the attackers know the salt, they can quickly crack weak or common passwords by comparing hashed values.

    SHA-256 is a fast hashing algorithm, which means attackers can try many guesses per second to find the right password. Modern hardware, like GPUs, can crack these hashes very quickly if they have access to the database and the salt.

    The risk increases if users have used weak passwords or if the same passwords are used across multiple accounts. If attackers crack the hashes, they can gain access to user accounts, leading to potential data breaches in other systems.

    It's important to switch to a more secure password hashing method, like bcrypt or Argon2, which are designed to be slow and use a unique salt for each password. This makes it much harder for attackers to crack the passwords and reduces the risk of a successful attack.

- [What do we change?]()

    You need to change how you secure your passwords in the database. Instead of using one round of SHA-256 with a static salt, switch to a more secure method like bcrypt, Argon2, or PBKDF2. These algorithms are designed for hashing passwords and include features that make them resistant to attacks, such as adding a unique salt to each password and using multiple rounds of hashing.

    First, update your system to use one of these stronger algorithms for new passwords. When users log in or reset their passwords, rehash them with the new algorithm. This will gradually move your user base to more secure hashes over time.

    Also, review your access controls and permissions. Ensure that only trusted and necessary personnel have access to the database. Implement role-based access controls to limit who can see and manage sensitive data.

    Consider implementing multi-factor authentication (MFA) for your users. This adds an extra layer of security by requiring a second form of verification in addition to passwords, which helps protect accounts even if passwords are compromised.

    Finally, keep your software and systems updated with the latest security patches. Regular updates help protect against known vulnerabilities that attackers might exploit. Establish a routine for checking and applying these updates to maintain strong security.

### [4. What are the 6 aggregate functions of SQL?]()

SQL has six common aggregate functions that are used to perform calculations on a set of values, returning a single value. These functions are helpful for summarizing and analyzing data in a database.

The first one is `COUNT()`. This function counts the number of rows that match a specific condition. For example, you can use `COUNT()` to find out how many orders were placed in a particular month.

Next, we have `SUM()`. This function adds up the values in a column. It is useful for finding the total sales amount or the total expenses in a specific category.

Then, there's `AVG()`, which calculates the average value of a numeric column. You might use `AVG()` to find the average salary of employees in a department.

`MIN()` is another aggregate function that returns the smallest value in a column. It can be used to find the lowest price of a product or the earliest date in a list of events.

`MAX()` is similar to `MIN()`, but it returns the largest value in a column. You can use `MAX()` to find the highest score in a test or the latest date in a timeline.

Finally, there's `GROUP BY`, which isn't an aggregate function by itself but is used with these functions to group rows that have the same values in specified columns into summary rows. For example, you can group sales data by region and then use `SUM()` to find the total sales in each region.

These aggregate functions are essential tools in SQL for analyzing and summarizing data efficiently. They help extract meaningful insights from large datasets by performing calculations on the data.
    

<div class="border-gray-light border-top footer mt-5 pt-3 text-gray text-right">
    <em class="float-right text-gray-light">This site is open source.</em>
</div>
<link rel="stylesheet" type="text/css" href="{{ "/assets/css/dark-mode-override.css?v=" | append: site.github.build_revision | relative_url }}">