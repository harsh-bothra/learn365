# HTTP Parameter Pollution

Index | Section
--- | ---
**1** | [About the attack](#About-the-attack)
**2** | [Scenario](#Scenario)
**3** | [What can be achieved](#What-can-be-achieved)
**4** | [How to test](#How-to-test)
**5** | [References](#References)
___

### About the attack
```
HTTP Parameter Pollution attack tries to pollute or override the parameters in order to perform a malicious action or achieve a desired result. 
```


### Scenario
```
The main reason why this attack happens is lack of proper input sanitization and how various application server treats the parameters. 

This can be found at places where HTTP Parameters are sent such as:
1. GET Requests
2. POST Requests
3. Cookies

Generally, an attacker can use HPP vulnerabilities to [Ref: Accunetix Blog]
- Supersede existing hardcoded HTTP parameters.
- Alter/modify the intended app behavior.
- Access and potentially exploit variables that are not been controlled properly.
- Bypass WAFs rules

[As per OWASP WSTG]
HTTP Parameter Pollution tests the application's response to receiving multiple HTTP parameters with the same name; for example, if the parameter username is included in the GET or POST parameters twice.

Supplying multiple HTTP parameters with the same name may cause an application to interpret values in unanticipated ways. By exploiting these effects, an attacker may be able to bypass input validation, trigger application errors or modify internal variables values.

As HTTP Parameter Pollution (in short HPP) affects a building block of all web technologies, server and client-side attacks exist.
```

### What can be achieved
```
1. Authentication Bypass
2. Server/Client-Side Attacks
3. Filter Bypass
4. Business Logic Abuse
```


### How to Test
```
1. Suppose a banking application has the following URL to receive an amount: https://t.co/qeNtjtqZol?amp=1
2. Now an attacker add an additional parameter to pollute the url like following: https://t.co/t3wObY8jDS?amp=1
3. Now if the payment is sent to both the users, it is an issue.
- Try doing the following:
  1. Adding parameters with the same key:value pairs like: to=123&to=12345
  2. Adding parameter with incremental key:value pairs like: u1=harsh&u2=hbothra
```

### References
- https://www.acunetix.com/blog/whitepaper-http-parameter-pollution/
- https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/04-Testing_for_HTTP_Parameter_Pollution
- https://logicbomb-1.medium.com/bugbounty-compromising-user-account-how-i-was-able-to-compromise-user-account-via-http-4288068b901f
- https://shahjerry33.medium.com/http-parameter-pollution-its-contaminated-85edc0805654
- https://www.ikkisoft.com/stuff/HPParticle.pdf
- https://owasp.org/www-pdf-archive/AppsecEU09_CarettoniDiPaola_v0.8.pdf
- https://hackerone.com/reports/105953
- https://hackerone.com/reports/298265
- https://hackerone.com/reports/106024
