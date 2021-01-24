# Session Puzzling Attack

Also known as Session Variable Overloading Attack. <br>
An app-level issue that may allow an attacker to bypass authentication, elevate privileges, skip MFA, or exploit any related issues.

Index | Section
--- | ---
**1** | [About the attack](#About-the-attack)
**2** | [Scenario](#Scenario)
**3** | [How to test](#How-to-test)
**4** | [Practice](#Practice)
**5** | [How to test](#How-to-test)
___

### About the attack
```
- When an application utilizes the same session variable for multiple purposes, this can be abused by an attacker to trick the application and perform the action as an authenticated or privileged user.
- In Simple Words, For example, if the application generates a session identifier at an unauthenticated page and later that can be used to access the authenticated page, it is a session puzzling vulnerability.

```


### Scenario
```
- An attacker navigates to the /forget_pass page of the application.
- He provides the username of the victim user and initiate a password reset request and observes the application assigns a session identifier by looking at the cookies.
- Now, the attacker utilizes the same session identifier in cookies to access an authenticated page /my_profile and the page is accessed successfully with the victim user's information.
- This is Session Puzzling/Session Variable Overloading Attack.
```

### How to Test
```
- Always check for the session identifier generation at various unauthenticated or lower privileged pages and see if they can be used to access authenticated or higher privileged pages.
```

### Remediation 
```
- Session variables should only be used for a single consistent purpose.
```

### Practice

- https://owasp-skf.gitbook.io/asvs-write-ups/kbid-250-session-puzzling

### References
- https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/06-Session_Management_Testing/08-Testing_for_Session_Puzzling
- https://dzone.com/articles/using-session-puzzling-to-bypass-two-factor-authen
- https://medium.com/bugbountywriteup/hunting-session-overloading-d2ec860c49c0
- https://code.google.com/archive/p/puzzlemall/downloads
- https://medium.com/@maheshlsingh8412/session-puzzling-attack-bypassing-authentication-29f4ff2fd4f5
- https://deepsec.net/docs/Slides/2013/DeepSec_2013_Shay_Chen_-_The_Boomerang_Effect_-_Using_Session_Puzzling_To_Attack_Apps_From_The_Backend.pdf
