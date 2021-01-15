#  WebSocket Vulns (part - 2)

Index | Section
--- | ---
**1** | Testing for IDOR in WebSockets
**2** | Denial of Service
___
#### Testing for IDOR in WebSockets
```
1. Intercept WebSocket Communication.

2. Look for any pattern/trace of ID/UUID/user/role and another similar parameter that may uniquely define an object/entity.

3. Assume the WebSocket communication is of a chatting application and consists of a request, where the Attacker is sending a message to the victim. There is a parameter called "sid" which is the attacker's user id.

4. Now, change this "sid" to some victim B's "sid" and if Victim A receives a message from Victim B. That's an issue.

Look for all IDORs cases that you look for in normal HTTP workflow
```
#### Denial of Service
```
1. WS allows any number of connections to the target server.
2. This behavior can be abused by an attacker to exhaust resources and perform a Denial of Service Attack.

- Try sending multiple requests to initiate a WS connection in a short time, this may trigger some lagging in the app processing which can be lead to App Level DoS.
```