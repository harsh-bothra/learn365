#  CRLF Injection
Index | Section
--- | ---
**1** | Introduction
**2** | Attack Vectors
**3** | Tools
**4** | H1 Reports
**5** | References & Good Reads

___


#### Introduction
```
1. CRLF (Carriage Return Line Feed) is a sequence that is used to terminate a line in HTTP Protocol. CR (\r) LF (\n) is used for this purpose. 

2. \r\n signifies End of the Line in HTTP Protocol. 

3. In a CRLF injection vulnerability attack the attacker inserts both the carriage return and linefeed characters into user input to trick the server, the web application or the user into thinking that an object is terminated and another one has started. As such the CRLF sequences are not malicious characters, however they can be used for malicious intend.

```

#### Attack Vectors
```
1. Cross-Site Scripting

- Assume the application is vulnerable to CRLF Injection and allows an attacker to inject an arbitrary Request Header which is reflected in response as well. 
Ex: www.harshbothra.tech/somepage%0d%0aContent-Length:%200%0d%0a%0d%0aHTTP/1.1%20200%20OK%0d%0aContent-Type:%20text/html%0d%0aContent-Length:%2025%0d%0a%0d%0a%3Cscript%3Ealert(1)%3C/script%3E 

- This may result into a Cross-Site Scripting 

2. Injecting Arbitrary Cookies 

- Similar method can be used to inject arbitrary cookies in the applicaiton and cause unexpected behaviours. 

3. HTTP Response Splitting 

- Example: https://book.hacktricks.xyz/pentesting-web/crlf-0d-0a#an-example-of-http-response-splitting-leading-to-xss


4. Log Poisoning 

- An attacker can input fake log entries and try to mess up the logs by injecting various CRLF sequences. 
- Example: https://book.hacktricks.xyz/pentesting-web/crlf-0d-0a#an-example-of-crlf-injection-in-a-log-file

5. Web Cache Poisoning

- This attack can also be used to add arbitrary headers and cause cache posining. I'll discuss this more during Web Cache Poisoning Series.

```

#### Tools 

```
- https://github.com/dwisiswant0/crlfuzz

```
#### H1 Reports
```
a. https://hackerone.com/reports/858650
b. https://hackerone.com/reports/237357
c. https://hackerone.com/reports/217058
d. https://hackerone.com/reports/245485
e. https://hackerone.com/reports/590020
f. https://hackerone.com/reports/332708
g. https://hackerone.com/reports/53843
h. https://hackerone.com/reports/52042
i. https://hackerone.com/reports/446271

```
#### References & Good Reads

```
a. https://book.hacktricks.xyz/pentesting-web/crlf-0d-0a
b. https://medium.com/cyberverse/crlf-injection-playbook-472c67f1cb46
c. https://github.com/swisskyrepo/PayloadsAllTheThings/tree/master/CRLF%20Injection
d. https://medium.com/bugbountywriteup/bugbounty-exploiting-crlf-injection-can-lands-into-a-nice-bounty-159525a9cb62

```