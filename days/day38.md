#  Pentesting FTP Service
Index | Section
--- | ---
**1** | Introduction
**2** | Attack Vectors
**3** | References & Good Reads

___


#### Introduction
```
1. The File Transfer Protocol (FTP) runs on Port 21 by default.
2. It is a standard network protocol used for the transfer of computer files between a client and server on a computer network.
3. It is a plain-text protocol that uses as new line character 0x0d 0x0a so it's important to connect using telnet instead of nc.

```

#### Attack Vectors
```
1. Weak Credentials

- If you discover a remote FTP Server accessible during Pentesting Engagement, always check for the default credentials.
- Always brute-force for the known username and passwords for FTP Servers.

2. FTP Anonymous Login

- Try logging in to the FTP Server with one of following Pair of credentials: 

    anonymous : anonymous
    anonymous : 
    ftp : ftp
- FTP Server are often exposed and are misconfigured to allow anonymous logins.
- Sometime you may also have more than read access i.e. write access as well allowing you to increase the impact further.

3. Enumerating for FTP Service

- Nmap: nmap -sV -sC -Pn -A -T4 -p21 <ip>
- Browser connection: ftp://anonymous:anonymous@10.10.10.98

4. Shodan Dorks

- ftp
- port:21

5. Known Vulnerabilities

- Always check for the known vulnerabilities in the FTP Server used based on the banner grabbing results.

6. FTP Bounce Attack

- Some FTP servers allow the command PORT. This command can be used to indicate to the server that you wants to connect to other FTP server at some port. Then, you can use this to scan which ports of a host are open through a FTP server.

- Read: https://book.hacktricks.xyz/pentesting/pentesting-ftp#ftpbounce-attack

```

#### References & Good Reads

```
a. https://book.hacktricks.xyz/pentesting/pentesting-ftp#ftpbounce-attack
b. https://www.hackingarticles.in/ftp-penetration-testing-windows/
c. https://www.hackingarticles.in/ftp-penetration-testing-on-ubuntu-port-21/
d. https://www.mindpointgroup.com/blog/cyber-security/conducting-and-detecting-data-exfiltration/
e. https://www.briskinfosec.com/blogs/blogsdetail/FTP-Penetration-Testing

```