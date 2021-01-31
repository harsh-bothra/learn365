#  Captcha Bypass Techniques
Index | Section
--- | ---
**1** | Introduction
**2** | Captcha Bypass Techniques
**3** | References
___
#### Introduction
```

1. Captcha is widely adapted by the applications to avoid automated attempts on a specific functionality, commonly on the Authentication forms to avoid brute-force attacks. 
2. However, it is possible to bypass Captcha and sometimes if the function is critical, it can be paid well in terms of bounties. 


```


#### Captcha Bypass Techniques
```

1. Missing Server Side Validation of the Captcha Field

- Some applications send Captcha Parameters on the client side but they do not validate this on the server side. 
- Simply, Remove the "Captcha" parameters and see if the request is processed successfully. 
- If yes, you can now use this request to perform your brute-force or rate limiting attempts. 

2. Missing Captcha Field Integrity Checks

- There are multiple scenarios around this one, this happens when the application validate whether the captcha parameters are present but not the "value".
- Simply, send an empty captcha parameter and see if the request works successfully.
- Change some specific characters of the captcha parameter and see if it possible to bypass the restriction. This usually happens when only string length is validated at the server-side.

3. HTTP Verb Manipulation

- If a request with POST method is using the Captcha, try changing the verb(method) from POST to GET and remove the captcha parameter.
- Often this bypasses the restrictions if the validation on the server-side are not in place.

4. Content Type Conversion 

- Change the content type from one type to another say from JSON to Plain Text and remove the captcha parameters to see if the request works successfully.

5. Reusuable Captcha 

- Just repeat the request using the same Captcha key multiple times and see if that works.
- One of my weird finding was, Capture the Request in Burp Proxy and send it to Intruder. Hold the request in Proxy Tool don't let it go.
- Run the Intruder and observed that same captcha can be reused any no. of time until you drop off the original request from proxy. 

6. Using HTTP Request Headers 

- Using Headers such as X-Forwarded-For, X-Original-IP, etc. you can try to bypass the Captcha in some cases. 

7. Some Other Techniques 

- Automated Captcha Solving Techniques such as OCR Enabled Bots and Human-Based Captcha Solving Services.

```


#### References

```
a. https://book.hacktricks.xyz/pentesting-web/captcha-bypass
b. https://medium.com/@honeyakshat999/captcha-bypass-techniques-f768521516b2
c. https://cobalt.io/vulnerability-wiki/v2-authentication/captcha-bypass-x-forwarded-for
d. https://medium.com/bugbountywriteup/bypassing-captcha-like-a-boss-d0edcc3a1c1
e. https://www.codementor.io/@harshittyagi/solving-captcha-with-web-automation-10v3rnvrf9
f. https://www.blackhat.com/docs/asia-16/materials/asia-16-Sivakorn-Im-Not-a-Human-Breaking-the-Google-reCAPTCHA-wp.pdf
g. https://www.iosrjournals.org/iosr-jce/papers/Vol22-issue3/Series-4/D2203042329.pdf
```
