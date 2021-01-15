#  Cache Poisoned Denial of Service (CPDos)


Index | Section
--- | ---
**1** | What is CPDos
**2** | Working
**3** | Types of CPDoS Attacks
**4** | HTTP Header Oversize
**5** | HTTP Meta Characters (HMC)
**6** | HTTP Method Override Attack
**7** | References & Reports
___
#### What is CPDos
```
One of a kind of Web Cache Poisoning attack that affects the resources used by an application to create a denial of service situation.

AIO Resource: https://cpdos.org 
```
#### Working
```
The working of this attack is theoretically very simple to understand:

1. The attacker sends a request to the server containing a malicious header with a malicious value. This can be any random header. 
ex: x-mal-example: tohackthehacker

2. This request is first processed by the intermediate cache server to check if the copy exists. 

3. The cache server forwards the attacker's request with malicious headers to the origin server as it doesn't store a fresh copy of the requested resource.

4. At the origin server, when this request comes, due to a malformed req bcz of a malicious header, the origin server returns an error page back to the intermediate cache server. 

5. The cache server stores this error page considering it as a fresh copy of the req resource

6. Whenever someone visits this page next after the cache is poisoned they are presented with the error page/message instead of original content.
This issue doesn't affect the integrity of the origin server but the cache server is fooled to store an invalid page that is served to the legitimate user making the original content unavailable.
```
#### Types of CPDoS Attacks
```
1. HTTP Header Oversize (HHO)
2. HTTP Meta Character (HMC)
3. HTTP Method Override (HMO)

- It is possible to perform a CPDoS attack by abusing Hop-by-Hop Headers.
```
#### HTTP Header Oversize
```
The HTTP Standard hasn't defined any size limit for the HTTP Request Headers. This thing can be utilized by an attacker to perform a multitude of attacks. This is the base for HHO based CPDoS Attack.

- HHO CPDoS attacks work in scenarios where a web app uses a cache that accepts a larger header size limit than the origin server.

- A malicious client sends an HTTP GET request including a header larger than the size supported by the origin server but smaller than the size supported by the cache.

- Working is similar to the above-described method, however, the header is sent like this: 
X-Oversized-Header-x: Big_Value 

- Upon receiving this the origin server will not be able to handle this and will return with Header Size Exceeded message which will be cache and displayed to the end-user.
```
#### HTTP Meta Characters (HMC)
```
This is again a similar technique the only difference is that in a malicious header, you send some harmful meta characters such as \n \r \a, etc.

- The origin server will not process these characters and may throw an error like character not allowed which will be presented to the victim user.

- The malicious header can be like this: 
X-Meta-Malicious-Header: \r\n
```
#### HTTP Method Override Attack
```
There are several headers present in HTTP Standard that allow modifying overriding the original HTTP header as the request goes forward through proxies before reaching the origin server. Some of these headers are:

1. X-HTTP-Method-Override
2. X-HTTP-Method
3. X-Method-Override

When these headers are supplied and supported, the header instructs the application to override the HTTP method in request to the header mentioned in these headers upon reaching the Origin Server.

This can be abused to perform a Cache Poisoned Denial of Service Attack. The steps to perform the attack are the same, only the used HTTP headers change. 

- The malicious header will look like this: 

X-HTTP-Method-Override: DELETE

- Now if the origin server doesn't support the DELETE method, it will return with Method Not Supported error which will be stored at intermediate cache & will be displayed to the legitimate users.
```
#### References & Reports
```
1. https://hackerone.com/reports/409370
2. https://hackerone.com/reports/728664
3. https://hackerone.com/reports/921704
4. https://hackerone.com/reports/326639
5. https://hackerone.com/reports/591302
```