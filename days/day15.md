#  WebSocket Vulns (part - 3)

Index | Section
--- | ---
**1** | Insecure WS Connection
**2** | Cross-Site Scripting
**3** | Sensitive Information in WS
**4** | Server-Side Injections
**5** | Other Server-Side issues
**6** | Learn & Practice
**7** | References
___
#### Insecure WS Connection
```
- If the WS is using WS:// instead of WSS://, this is like using HTTP:// instead of HTTPS://. 
- The WSS:// sends the traffic over SSL/TLS & prevents MiTM attacks.
- If any sensitive action is happening through WebSocket over WS://, try traffic intercepts, and create a proof of concept to show the impact.
- If the WebSocket is using WSS://, try degrading it to WS:// and see if the WS:// is supported.
```
#### Cross-Site Scripting
```
- Check if the WebSocket is sending data that is displayed back on the application interface or somewhere in another panel (if you have access to it)
- Also, if the data is reflecting somewhere else say admin panel, always try to perform Blind XSS
- Send XSS payloads in interesting parameters & if the app fails to perform Input Validation in WS, it can allow an attacker to trigger XSS.
```
#### Sensitive Information in WS
```
- Read the Message sent through WS & keep an eye for any sensitive information that can be utilized
- Just like reading response or JavaScript files in the usual web workflow. 
```
#### Server-Side Injections
```
- Check all the WebSocket Parameters for potential Server Side Injection like SQLi 
- Fuzz the Parameters based on how various payloads and inputs are handled.
```
#### Other Server-Side issues
```
It is always a good idea to test the interesting parameters for all potential security vulnerabilities that are usually tested in normal HTTP Workflow.
```
#### Learn & Practice
```
PortSwigger: https://portswigger.net/web-security/websockets
```
#### References
```
- https://hackerone.com/reports/178990
- https://hackerone.com/reports/409850
- https://hackerone.com/reports/395729
- https://hackerone.com/reports/163464
- https://github.com/github/securitylab/issues/65
- https://hackerone.com/reports/512065
- https://hackerone.com/reports/1023669
- https://hackerone.com/reports/86283
```