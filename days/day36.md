#  Pentesting Rsync Service
Index | Section
--- | ---
**1** | Introduction
**2** | Enumeration & Issues
**3** | References & Good Reads

___


#### Introduction
```
1. Rsync is a tool for performing trasnfer and sync between two servers. 
2. It is usually used on Linux systems.
3. Sync is determined by checking the file sizes and timestamps. 
4. It is usually found running on Port - 873
5. However, due to the weak configurations, it is often an interesting attacker vector to gain unauthorized access to sensitive data, and sometimes the means to obtain a shell on the system.
6. Remotely accessing directories shared through Rsync requires two things, file share access and file permissions.

	a. File Share Access can be defined in /etc/Rsyncd.conf to provide anonymous or authenticated access.
	b. File Permissions can also be defined in /etc/Rsyncd.conf by defining the user that the Rsync service will run as. If Rsync is configured to run as root, then anyone allowed to connect can access the shared files with the privileges of the root user.
```

#### Enumration & Issues
```
1. Finding a Rsync Server 
> Run a port scan using nmap, you can use below command: 
> nmap -sS -sV -p873 <ip> 

2. Enumeration Steps 
(change 127.0.0.1 to your target IP)

a. List Directory
>  rsync 127.0.0.1:: 

b. List Sub Directory
> rsync 127.0.0.1::files

c. List Directories & Files Recursively
> rsync -r 127.0.0.1::files/tmp/

d. Downloading Files & Folders

> rsync 127.0.0.1::files/tmp/test.txt .
> rsync -r 127.0.0.1::files/tmp

e. Uploading Files & Folders

> rsync ./file.txt 127.0.0.1::files/test
> rsync -r ./folder 127.0.0.1:files/test

3. More Interesting Enumeration Techniques: 
> https://blog.netspi.com/linux-hacking-case-studies-part-1-rsync/
> https://book.hacktricks.xyz/pentesting/873-pentesting-rsync#post

```
#### References & Good Reads

```
a. https://bitvijays.github.io/LFF-IPS-P2-VulnerabilityAnalysis.html#rsync-port-873
b. https://blog.netspi.com/linux-hacking-case-studies-part-1-rsync/
c. https://medium.com/@minimalist.ascent/enumerating-rsync-servers-with-examples-cc3718e8e2c0

```