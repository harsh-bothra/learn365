# CORS Misconfiguration
Index | Section
--- | ---
**1** | Introduction
**2** | Important Headers
**3** | Exploitation Cases
**4** | Labs
**5** | Tools
**6** | H1 Reports
**7** | References & Good Reads

___


#### Introduction
```
- As per WikiPedia, Cross-origin resource sharing (CORS) is a mechanism that allows restricted resources on a web page to be requested from another domain outside the domain from which the first resource was served. A web page may freely embed cross-origin images, stylesheets, scripts, iframes, and videos.

- CORS is not a security vulnerability. Often interviewers trick on this question.

- Misconfigured CORS is a security vulnerability. 

- This is often a tricky question asked in cyber security interviews.

```

#### Important Headers
```
1. Access-Control-Allow-Origin

- This Header defines what all origins are allowed to perform a CORS request. 
- The specification allows for null, single, multiple and wildcard origins. 
- However, no browser supports multiple origins and there are restrictions on the use of the wildcard *.(The wildcard can only be used alone, this will fail Access-Control-Allow-Origin: https://*.normal-website.com and it cannot be used with Access-Control-Allow-Credentials: true)
- This Header is observed in the Response Headers and is a result of "Origin" header in the Request. 
- An attacker tries to abuse the "Origin" header in the Request by changing origin to the attacker controlled origin and if ACAO header reflects the attacker supplied origin, it's a CORS Misconfiguration (but not talking about exploitation yet).

2. Access-Control-Allow-Credentials

- This usually contains "true" or "false" values and tells if the reading response is permitted or not. 


```

#### Exploitation Cases 

```
1. Arbitrary Origin Reflected & Credentials set to True

a. An attacker supplied "Origin" header is reflected in the Response Headers.
b. Access-Control-Allow-Credentials is set to "true"
c. This is the exploitable case and easily be exploited. 


2. Misconfigured Whitelisting

a. Assume that the "origin" header defined by the target allows any domain ending with "harshbothra.tech"
b. As a result of poorly implemented whitelist, an attacker can try providing following domain in the "origin" header like "attacker-harshbothra.tech" and if it reflects successfully, there's an issue with the implemented whitelist.

3. Null Origin 

a. If "Null" is accepted in the "Origin" header and is reflected back, this can be abused by an attacker. 


4. Some other Attack Scenarios with CORS: 

a. Breaking TLS with poorly configured CORS
b. Exploiting XSS via CORS trust relationships
c. Intranets and CORS without credentials

```


#### Labs 
```
- https://portswigger.net/web-security/cors
```

#### Tools 

```
- https://github.com/chenjj/CORScanner
- https://github.com/s0md3v/Corsy
- https://github.com/Shivangx01b/CorsMe
```

#### H1 Reports 

```
- https://hackerone.com/reports/235200
- https://hackerone.com/reports/426165
- https://hackerone.com/reports/426147
- https://hackerone.com/reports/769058
- https://hackerone.com/reports/896093
- https://hackerone.com/reports/470298
- https://hackerone.com/reports/733017
```

#### References & Good Reads 

```
a. https://portswigger.net/web-security/cors
b. https://book.hacktricks.xyz/pentesting-web/cors-bypass#pre-flight-request
c. https://portswigger.net/research/exploiting-cors-misconfigurations-for-bitcoins-and-bounties
d. https://medium.com/bugbountywriteup/think-outside-the-scope-advanced-cors-exploitation-techniques-dad019c68397
e. https://www.corben.io/advanced-cors-techniques/https://github.com/chenjj/CORScanner

```