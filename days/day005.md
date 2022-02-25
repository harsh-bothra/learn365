#  Client-Side Template Injection (CSTI)
Index | Section
--- | ---
**1** | What is CSTI
**2** | Method

___
#### What is CSTI
```
1. This occurs at the client-side like other JS attacks such as XSS.
2. This is mainly seen in the various JS libraries like AngularJS, VueJS etc which utilize the template engines at the client-side.
3. The presence of "ng-app" in the page source identifies the use of templates. 
4.  If the application directly accepts the input and process it without any validation, it may be vulnerable to CSTI. 
5. CSTI leads to perform cross-site scripting attacks by escaping
6. Testing this issue is similar to Server-Side Template Injection. 
```
#### Method
```
a. In the suspected field, provide a payload like {{11*5}}
b. If the response reflected is 55, this tells that there is the use of the template and further you can try performing CSTI to XSS
```
