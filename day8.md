#  Json Padding (JSONP) Attack
Index | Section
--- | ---
**1** | What is JSONP & JSONP Attack
**2** | Callback Parameter
**3** | Security Risks with JSONP
**4** | Tools
**5** | References
___
#### What is JSONP & JSONP Attack
```
1. JSONP stands for  JavaScript Object Notation with Padding  which allows sending JSON data across domains without worrying about Cross-Domain Issues.

2. It utilizes <script> tag to perform the action instead of using XMLHttpRequest. However, the function requires to be existing in the global scope

3. JSONP is an insecure communication technique and it should only be used when no personal or sensitive data is involved and sanitizing the callback function.

4. There are multiple attacks affecting the JSONP implementation as it doesn't have a pre-implemented security feature. 


```

#### Callback Parameter
```
1. The “padding” or function to call with the JSON data, is often specified as a parameter. Often this parameter is called callback and is reflected as-is in the response.

```

#### Security Risk with JSONP
```

1. It is possible to access data cross-domains which makes it possible to steal sensitive information of an authenticated user which other domains should not have access to. JSONP attack makes it possible to retrieve the data in a CSRF-style attack.

2. Usually the JSONP endpoint will be visible by looking at the various GET/POST calls. Alternatively you can search your HTTP History to search for endpoints like ?callback=somedata, etc. 

3. JSONP might be supported at the API level and might not be visible directly or acts as a hidden parameter. You can try following: 
    A. Adding  a callback parameter to a JSON URL, by appending ?callback=something to the URL.
    B. When a format type is provided, change it to JSONP. Change ?format=json to ?format=jsonp.

```


#### Tools 

```
1. https://github.com/kapytein/jsonp
2. https://github.com/zigoo0/JSONBee

```


#### References

```
a. https://www.sjoerdlangkemper.nl/2019/01/02/jsonp/ 
b. https://gracefulsecurity.com/jsonp-vulnerabilities/
c. https://owasp.org/www-pdf-archive//2017-04-20-JSONPXSS.pdf	
d. https://gist.github.com/karanth/8467944
e. https://securitycafe.ro/2017/01/18/practical-jsonp-injection/
f. https://medium.com/bugbountywriteup/exploiting-jsonp-and-bypassing-referer-check-2d6e40dfa24
g. Sample JSONP Page to Practice the Retrieval of data using Script through Other Domain: https://demo.sjoerdlangkemper.nl/jsonp.php
h. https://hackerone.com/reports/10373
```
