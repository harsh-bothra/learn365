#  Cookie Based Authentication Vulnerabilities
Index | Section
--- | ---
**1** | Introduction
**2** | Cookie Based Authentication Vulnerabilities
**3** | MindMap: Got Cookies? Cookie Based Authentication Vulnerabilities 
**4** | References & Good Reads

___


#### Introduction
```
1. Cookie based session identification is a way to allow application to provide authentication mechanism for it's users.
2. However, these days Token based authentication is being widely used over Cookie Based Authentication due to a large attack surface that Cookie Based Authentication leaves open. 
3. Everyone working in the domain of penetration testing or application security is familiar to cookies and how they are being used. Let's talk about some of the vulnerabilities that are often found in Cookie Based Authentication.

```

#### Cookie Based Authentication Vulnerabilities
```
1. Cross-Site Scripting 

a. Assume that value of the Cookie Parameter "Name" is reflected in the application.
b. Change the "Name" value to "XSS Payload" and it may result into a XSS.

2. Insufficient Session Management

a. Session Doesn't Expire on Logout

- Server-Side Only
- Both Server-Side & Client-Side

b. Long Session Expiry
c. Session Doesn't Expire on Password Reset/Change
d. Concurrent Session/Parallel Login 

3. Session Fixation 

- An attacker tricks the victim user to use a Session Identifier which is known to the attacker. 
- Read: https://secureteam.co.uk/articles/web-application-security-articles/understanding-session-fixation-attacks/

4. Privilege Escalation 

a. Horizontal Privilege Escalation

i. Assume that the application uses Multi-Organization Model.
ii. Cookies are used to define which organization a user can access.
iii. Alter the Cookies in order to Access some other Organization.

b. Vertical Privilege Escalation 
i. Assume that the cookies are used to determine the "Role" of the User.
ii. Alter the Cookies in order to Elevate the "Role" of the User.

c. Similarly, Try if the Lower user's cookies can be used to access Higher User's Functions or Try if the cookies of Organization 1 user can be used to Access functions of Organization 2.

5. Insecure Direct Object Reference

a. If the cookies are using some access defining parameter such as "user_id"
b. Change the value of these parameter in order to check if you can access other user's data.

6. Missing Cookie Security Attributes

a. Missing HTTPOnly Flag
b. Missing Secure Flag
c. Missing Same-Site Flag

7. Guessable/Weak Cookie

a. Check if the cookies are not generated Randomly by issues multiple cookies and analyzing them.
b. Check if some weak/known cryptography is used. Let's assume the cookies are using Base64 Encoding and can be decoded/forged easily.

8. File Inclusion

a. If a cookie is used to define some server-side attribute that can be controlled by a user, try for File Inclusion Attacks.
b. Read: https://medium.com/@tehmezovismayil/cookie-based-php-local-file-inclusion-bug-bounty-553f8b38d4dc

9. Session Puzzling 

a. When an application utilizes the same session variable for multiple purposes, this can be abused by an attacker to trick the application and perform the action as an authenticated or privileged user.
b. Read: https://github.com/harsh-bothra/learn365/blob/main/days/day17.md

10. Padding Oracle Attack

a. Read: https://book.hacktricks.xyz/pentesting-web/hacking-with-cookies#advanced-cookies-attacks

11. CBC-MAC/ECB Encryption

a. Read: Read: https://book.hacktricks.xyz/pentesting-web/hacking-with-cookies#advanced-cookies-attacks

12. Authentication Bypass (Cookies are not Validated)

a. Try accessing a protected resource by removing cookies.
b. If the resource is accessible via GET Request, try for Direct Request (Forceful Browsing) with unauthenticated user.

13. SQL Injection

a. Read: https://resources.infosecinstitute.com/topic/cookie-based-sql-injection/

14. Denial of Service - Cookie Bomb

a. Forcing the server to process cookies larger than the restricted cookie size defined by the server may cause Denial of Service Attack.
b. Read: https://blog.innerht.ml/tag/cookie-bomb/

15. Parameter Pollution

a. Assume that the cookies utilize a parameter called "user_id=" to retrieve some data.
b. However, the application is not vulnerable to IDOR and changing "user_id=" to victim value, doesn't help out.
c. Attacker, add an additional "user_id=" parameter value to the cookie with victim's user ID. Like: "user_id=attacker&user_id=victim" 
d. Three things can happen here:
    - The application may retrieve data of Victim User. 
    - The Application may retrieve data of both Attacker & Victim User.
    - The Application is not vulnerable and doesn't return anything.

16. Mass Assignment 

a. Similar to the Parameter Pollution, However, in this, Attacker tried to Inject multiple User ID in same user_id parameter.

17. Arbitrary Cookie Injection

a. Try Injecting some Arbitrary Cookies using Attacks such as CRLF Injection.
b. Sometimes it can be used to escalate privilege or if the application malfunction, it can reveal sensitive information through Stack Traces.

18. Insecure Deserialization

a. If cookies are using Serialized Objects, try performing Insecure Deserialization Checks.
b. Read: https://portswigger.net/web-security/deserialization/exploiting

19. Cookie Length Violation

a. It may cause attacks such as Buffer Overflows
b. Read: https://docs.imperva.com/bundle/on-premises-knowledgebase-reference-guide/page/cookie_value_length_violation.htm

20. Session Donation

a. Read: https://book.hacktricks.xyz/pentesting-web/hacking-with-cookies#session-donation

21. Sensitive Data Stored in Cookies

a. Check if any PII or Other Sensitive Information Stored in Cookies
b. This information usually includes: Email, Date of Birth, Mobile, Address, SSN, Etc.

```

#### MindMap: Got Cookies? Cookie Based Authentication Vulnerabilities 

```
MindMap: http://www.xmind.net/m/2FwJ7D

```

#### References & Good Reads

```
a. https://book.hacktricks.xyz/pentesting-web/hacking-with-cookies
b. https://docs.imperva.com/bundle/on-premises-knowledgebase-reference-guide/page/cookie_value_length_violation.htm
c. https://portswigger.net/web-security/deserialization/exploiting
d. https://blog.innerht.ml/tag/cookie-bomb/
e. https://resources.infosecinstitute.com/topic/cookie-based-sql-injection/
f. https://github.com/harsh-bothra/learn365/blob/main/days/day17.md
g. https://medium.com/@tehmezovismayil/cookie-based-php-local-file-inclusion-bug-bounty-553f8b38d4dc
h. https://secureteam.co.uk/articles/web-application-security-articles/understanding-session-fixation-attacks/

```