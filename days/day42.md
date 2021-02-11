# Race Conditions
Index | Section
--- | ---
**1** | Introduction
**2** | Attack Vectors
**3** | Tools 
**4** | References & Good Reads

___


#### Introduction
```
1. Race Conditions are interesting logical issues which are occur due to confusion in processing a limited resource parallely. 
2. This issue is often found at the places where performing an action is limited to certain number of times only. 
3. For Example: You can only invite 10 users from one account but the race condition issue may allow you to invite more.

```

#### Attack Vectors
```
1. Business Logic Abuse 

a. Assume an applicaton restricts no. of times a function can be used, let's say, sending an invite is limited to 10.
b. An attacker tries to parallely open 100s of threads and try to send multiple invites at once.
c. If the application is vulnerable, the user will be able to send more than 10 invites.

2. Race Conditions in OAuth2

- Read: https://book.hacktricks.xyz/pentesting-web/race-condition#oauth2-eternal-persistence


~ Usually this issue cause Business Logic Abuse, hence, all such functionalities which are attempt restricted can be bypassed using this attack. Thus, not creating separate attack vectors for this.
```

#### Tools

```
- Burp Intruder
- Burp Turbo Intruder Plugin

```

#### References & Good Reads

```
a. https://medium.com/@pravinponnusamy/race-condition-vulnerability-found-in-bug-bounty-program-573260454c43
b. https://hackerone.com/reports/759247
c. https://book.hacktricks.xyz/pentesting-web/race-condition#oauth2-eternal-persistence

```