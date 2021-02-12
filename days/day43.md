# SMTP Open Relay Attack
Index | Section
--- | ---
**1** | Introduction
**2** | How to Test
**3** | References & Good Reads

___


#### Introduction
```
1. If you have found SMTP port open, the next thing you should check for is "SMTP Open Relay".
2. SMTP relay is a mail server through which we can send Outbound emails.
3. SMTP service is often found on Port 25, 465 & 587.

```

#### How to Test
```
1. Using Metasploit
a. run msfconsole
b. use auxiliary/scanner/smtp/smtp_relay
c. show options
d. set required options
e. run
f. The output will show if the Open Relay is present. 


2. Manually Exploiting Open Relay

- Assuming the Open Relay is present. Do following steps:
a. telnet <server_ip> 25
b. HELO target.com
c. HELO harshbothra.tech
d. MAIL FROM: admin@target.com
e. RCPT TO: harsh@harshbothra.tech
f. DATA
g. This is an email from Open Relay
h. .


3. Using Nmap NSE
-  nmap -sV --script smtp-open-relay -v <target>

4. Find SMTP Services using Shodan
- port:25
- "smtp"

```


#### References & Good Reads

```
a. https://www.blackhillsinfosec.com/how-to-test-for-open-mail-relays/
b. https://www.rapid7.com/db/modules/auxiliary/scanner/smtp/smtp_relay/

```