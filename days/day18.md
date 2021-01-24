# Mass Assignment Attack

Index | Section
--- | ---
**1** | [About the attack](#About-the-attack)
**2** | [Scenario](#Scenario)
**3** | [How to test](#How-to-test)
**3.1** | [Steps](#Steps)
**4** | [What can be achieved](#What-can-be-achieved)
**5** | [How to test](#How-to-test)
**6** | [Practice](#Practice)
**7** | [References](#References)
___

### About the attack
```
Occurs when an app allows a user to manually add parameters in an HTTP Request & the app process value of these parameters when processing the HTTP Request & it affects the response that is returned to the user. 
```


### Scenario
#### Original Request
```
POST /userinfo
<redacted>

username=harsh
```
#### Response
```
200 OK 
<redacted>

username=harsh&isadmin=false&email=harsh@harshbothra.tech
```

#### Modified Request 
```
POST /userinfo
<redacted>

username=harsh&isadmin=true
```

#### Response of Modified Request
```
200 OK 
<redacted>

username=harsh&isadmin=true&email=harsh@harshbothra.tech
```

***Now consider the above example where an attacker observes normal request/response flow and notice there is a parameter called isadmin which is set to false.***

***The attacker tries to send "isadmin" with the value true in the HTTP request and as a result, in response, the "isadmin" parameter is now true and the normal user is now an admin user.***
- This is a simple example of Mass Assignment Vulnerability.

### How to Test
```
Depending on the language/framework this issue has different names: 
- Mass Assignment: Ruby on Rails, NodeJS.
- Auto binding: Spring MVC, ASP NET MVC.
- Object injection: PHP.
```
#### Steps
- Capture the Request and Observe its response.
- Include the parameters present in Response to the HTTP Request with the modified values.
- Observe if the values in response are changed as Modified values.
- Navigate to the application and observe if the changes are also reflected on the UI level.


### What can be achieved
- Authentication Bypass (2FA) - Adding "Success":true parameter in the request with the wrong OTP.
- Privilege Escalation - Changing the Role/Access Level.
- Modifying/Overwriting Sensitive Information.
- Client-Side/Server-Side validation might be missing in the parameters that are not editable by the user from the UI level and if can be abused through mass assignment, it can lead to exposure to some serious issues.
- Premium Feature Abuse/Bypass Payment Restrictions.


### Practice

- https://owasp-skf.gitbook.io/asvs-write-ups/kbid-147-parameter-binding

### References
- https://cheatsheetseries.owasp.org/cheatsheets/Mass_Assignment_Cheat_Sheet.html
- https://virtuesecurity.com/kb/api-mass-assignment/
- https://itzone.com.vn/en/article/mass-assignment-vulnerability-and-prevention/
- https://hackerone.com/reports/99424
