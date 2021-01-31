# Common Business Logic Issues (Wrap)

Index | Section
--- | ---
**1** | [How to test](#How-to-test)
___

### How to Test
```
(Cont'd...)
9. Parameter Tampering 
- Tamper Payment or Critical Fields to manipulate their values
- Add multiple fields or unexpected fields by abusing HTTP Parameter Pollution & Mass Assignment
- Response Manipulation to bypass certain restrictions such as 2FA Bypass 

10. App Implementation Logic Abuse
- If an app accepts JSON data, try changing content type to XML and see if the XML data is being processed, it can be left vulnerable to XXE or XML-based attacks.
- If an application is using the DELETE method to delete a resource but there is no CSRF protection, try converting the method to GET/POST and add an additional parameter like ?method=delete
- In the above case if any user ID is going in the request, try bypassing method-based restrictions by adding parameters like X-Method-Override.
- If you see a UUID, try to replace with similar mapping such as 1,2,3.. often UUID mapping is accepted by the applications.
- Try the HEAD method to bypass the authentication restrictions. 

11. Denial of Service Situations 
- Resource Exhaustion
- Weak Account Lockout Mechanisms
- Kicking out a user/banning a user somehow from accessing the application.
- Application Level DoS by abusing the various functionalities present within the application.

In a nutshell, business logic absuse is a special class of vulnerabilities that I personally feel has no end.
Every application might have some different or special logics which are unique to them and it's always fun to abuse them and circumvent their original workflow.
```

