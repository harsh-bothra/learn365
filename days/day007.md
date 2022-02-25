#  Cross-Site Script Inclusion (XSSI)
Index | Section
--- | ---
**1** | Cross-Site Script Inclusion (XSSI)
**2** | Types of XSSI
**3** | Exploiting Authenticated Static JS & Dynamic JS
**4** | Some Interesting Attacks Descibed in OWASP Testing Guide using XSSI
**5** | Labs 
**6** | Tools
**7** | References
___

#### What is Cross-Site Leaks

```
1. XSSI is a different attack vector than XSS. In XSS, the payload is included on the victim to perform an action. However, In case of XSSI the victim's code (JS) is embedded in the attacker controlled page. 

2. In XSSI, the goals is to usually steal the data bypassing the restrictions such as Same Origin Policy (SOP)

3. XSSI is less utilized and I personally never paid much attention to this attack vector. However, this seems to be an interesting and realistic, easy to exploit attack vector. 

4. This attack is to mainly target the sensitive information that might get dynamically stored in the javascript files when a user perform some activity. If there are not proper restrictions set, an attacker can easily read and get hold of sensitive information. However, this can also be utilized to steal other information such as authentication tokens.

```

#### Types of XSSI

```
There are mainly Four Situations when it comes to XSSI attack: 

1. Regular XSSI - Static Javascript
- This is similar to looking for the hardcoded data in a javascript file.
- Since the javascript file is static, an attacker can try to embed it a page in order to extract information. 
2. Authenticated Access to Static Javascript
3. Dynamic Javascript
4. Non-Script Attack
```

#### Exploiting Authenticated Static JS & Dynamic JS

```
1. In case of Dynamic JS, the sensitive information is added to the Javascript file when the user performs an action. 
2. In Order to test this:
	A. Perform an action with authenticated user.
	B. Perform the same action with unauthenticated user.
	C. Compare the content of JS files included in the response in both cases. If there is difference it may give an idea of dynamic JS being used. 
3. To Automatically detect this attck: 
	A. Use Detect DynamicJS Burp Plugin
		a. This works on the same principle. Passively scanning all JS files and than scanning those files without authentication identifier like cookies. 
		b. If issue is found, it will be seen under Target Tab as Informational severity finding. 
```


#### Some Interesting Attacks Descibed in OWASP Testing Guide using XSSI

```
1. Sensitive Data Leakage via Global Variables
2. Sensitive Data Leakage via Global Function Parameters
3. Sensitive Data Leakage via CSV with Quotations Theft
4. Sensitive Data Leakage via JavaScript Runtime Errors
5. Sensitive Data Leakage via Prototype Chaining Using 'this'

```

#### Labs 

```
1. https://google-gruyere.appspot.com/part3
```

#### Tools 

```
1. https://github.com/luh2/DetectDynamicJS
```

#### References

```
a.https://www.scip.ch/en/?labs.20160414
b. http://sebastian-lekies.de/leak/
c. https://owasp.org/www-project-web-security-testing-guide/v41/4-Web_Application_Security_Testing/11-Client_Side_Testing/13-Testing_for_Cross_Site_Script_Inclusion.html
d. https://www.mbsd.jp/Whitepaper/xssi.pdf
e. https://medium.com/bugbountywriteup/effortlessly-finding-cross-site-script-inclusion-xssi-jsonp-for-bug-bounty-38ae0b9e5c8a
f. https://www.usenix.org/system/files/conference/usenixsecurity15/sec15-paper-lekies.pdf

```
