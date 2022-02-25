#  JSON Attacks
Index | Section
--- | ---
**1** | What is JSON and its Attack Surface
**2** | Interesting JSON Attacks
**3** | References
___
#### What is JSON and its Attack Surface
```
1. JSON is widely used in modern web applications and often most of the API requests are observed using JSON as data type. Some applications use it for communicate data where some applications use it to store data. 

2. Use of JSON is mostly observed in REST APIs and AJAX applications.

3. JSON is however considered to be secure than traditional data exchange formats like text/plain but it also comes with multiple security issues if not implemented properly. 

4. Most of the Server Side JSON attack happens when an attacker is able to supply untrusted data and the server without performing sanitization, writes it directly to JSON Stream. 

5. On the other hand, In case of Client-Side JSON attacks are a result of user supplied data getting parsed using JavaScript eval() function without any sanitization. 

```

#### Interesting JSON Attacks
```
1. JSON Deserialization Attack 

- It is possible to perform and exploit deserialization attack in JSON implementation. The following Research Paper is the goldmine to learn about it: https://www.blackhat.com/docs/us-17/thursday/us-17-Munoz-Friday-The-13th-JSON-Attacks-wp.pdf


2. JSONP (JSON Padding) Attack

- I described this attack on Day-8 of Learn365, can be found in Day-8.MD 

3. Brute-Forcing Attacks

- It is possible to perform attacks that fall under brute-force category such as testing for No Rate Limiting, Lockout Policy, etc. in JSON. The steps are similar to traditional web app approaches. 

4. XXE 

- By changing the content-type to XML, it might be possible to perform XXE if the application doesn't sanitize and validate user supplied Input. 

# Steps: 

    1. Capture a Request with JSON Body
    2. Change content type to application/xml and insert a XML payload 
    3. Also, you can use Burp's Content Type Convertor plugin.
    4. Observe how application responds and perform attack based on response. 

5. XSS

- The JSON implementation might be vulnerable to traditional XSS attacks if there is no input validation/sanitization in place. It's always a good idea to fuzz the application and try checking manually how application reacts on supplying different Payloads 

6. Injection Attacks 

- Again, if there is a lack of input validation and application doesn't perform proper checks, it is possible to perform any sort of inject attacks such as SQL Injection, Command Injection, etc. based on how application works. 

- It's always a good idea to check how the application reacts upon supplying different payloads. 

7. File Inclusion/File Read 

- If the application utilize a weakly implemented function that let a user read files, it can be abused to perform Local File Read. 

- For Ex: Original Request Body

    {"user":"admin", "path"="/admin.html"}

- If the path parameter is not getting validaed, it can be abused to perform local file read like: 

    {"user":"admin", "path"="../../../../../../../../../../../etc/passwd"}


8. Broken Access Controls & Logical Issues 

- Similar to the other implementation, JSON implementation can also be vulnerable to BAC and other Logical Issues as this is more of the responsibility of developer to ensure how various logics and centralized checks are handled. 

9. CSRF 

- It is possible to perform CSRF in JSON based implementation but it maybe tricky sometimes. 

# Example (Refered from websecgeeks.com)

    POST /site/getuserinfo HTTP/1.1
    Host: websecgeeks.com
    Content-Type: application/json;
    Cookie: test=test;

    {"id":"1","email":"attacker@attacker.com"}


- We can perform the CSRF for this request as mention below.
    <html>
    <form action="" method=post enctype="application/json" method="POST">
    <input name='{"id":"1","email":"attacker@attacker.com"}' type='hidden'>
    <input type=submit>
    </form>
    </html>

10. JSON Hijacking Attack

- This looks similar to JSONP attacks but it different a way that application does not provide a convenient callback function. Instead, the attack relies on modifying native JS objects. However, this is not possible anymore in current browsers.

11. Other Common Vulnerabilities that may affect JSON implementation:

    a. Mass Assignment
    b. Open Redirection
    c. Parameter Tampering 
    d. Response Manipulation
    e. Session Related Issues 

12. Some Other Interesting JSON Attacks 
(As described in the following paper: http://www.infosecwriters.com/Papers/ASood_ExploitingJSON.pdf) 

    a. String Defracturing Attack 
    b. Malicious Hashing & Listing 
    c. Fused Proxy Attack: Domain Crossing
    d. JSON-XML Banner Grabbing

```


#### References

```
a. https://owasp.org/www-pdf-archive/Marshaller_Deserialization_Attacks.pdf.pdf
b. https://www.websecgeeks.com/2015/10/attacking-json-application-pentesting.html
c. https://medium.com/@koumudi.garikipati/json-based-xss-84089141c136

```
