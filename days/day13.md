#  WebSocket Vulns

WebSocket is a network protocol that enables 2-way communication b/w client & server. \
In the HTTP standard, where the one-party has to wait for the req./res from another party before performing the next action. 

The major goal of WebSocket is to enable real-time communication and can widely be seen in IM applications. 

I will be diving the WebSocket learning into 3 parts and I will post more about various attacks in the next two days.


Index | Section
--- | ---
**1** | Web socket Protocol Scheme
**2** | WebSocket Connection Process
**3** | How to work with Websocket Messages
**4** | General Security Implications
**5** | References
___
#### Web socket Protocol Scheme
```
1. Websockets use wss:// and ws:// as the protocol scheme. 
2. This is similar to HTTPS and HTTP. Here, the WSS:// is a secure channel where WS:// is an insecure channel.
```
#### WebSocket Connection Process
```
1. The application will send an HTTP request with two additional Headers: Upgrade: WebSocket & Connection: Upgrade to the server. 
2. This request basically initiates the Web Socket connection process.
3. In return the server will return 101 Switching Protocols status code.
4. After this, WebSocket communication will start to take place. 
```
#### How to work with Websocket Messages
```
1. Burp Suite allows an option to capture the WebSocket Traffic, modify it, and replay it.
2. Additionally, you can use the Simple Web Socket browser extension to check for some test cases and communicating with the Web Socket. 
```
#### General Security Implications
```
1. Denial of Service 
2. Insecure Communication
3. Missing Access Controls & Authorization Checks
4. Missing Input Validation in User-Controlled Data 
5. Lack of/Improper Authentication 
6. Tunneling 
7. Cross-Site Web Socket Hijacking 
8. Server-Side Issues & OOB (out of band) Issues
```
#### References
```
WebSocket Top 7 Vuln: https://www.neuralegion.com/blog/websocket-security-top-vulnerabilities/
```