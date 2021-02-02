#  Pentesting Docker Registry
Index | Section
--- | ---
**1** | Introduction 
**2** | Discovery
**3** | Security Issues
**4** | References & Good Reads

___
#### Introduction
```
1. Docker is a computer program that performs operating-system-level virtualization, also known as "containerization".

2. The Docker Registry is a stateless, highly scalable server side application that stores and lets you distribute Docker images using HTTP API. Earlier versions of docker registry api i.e. v1 had a few problems and hence v2 was released and considerably improves security. 

3. However it should be noted that both versions of Docker Registry have no authentication enabled by default.
```


#### Discovery
```
1. The easiest way to discover this service running is get it on the output of nmap. Anyway, note that as it's a HTTP based service it can be behind HTTP proxies and nmap won't detect it.

2. Some fingerprints:
- If you access / nothing is returned in the response
- If you access /v2/ then {} is returned
- If you access /v2/_catalog you may obtain:
	{"repositories":["alpine","ubuntu"]}
	{"errors":[{"code":"UNAUTHORIZED","message":"authentication required","detail":[{"Type":"registry","Class":"","Name":"catalog","Action":"*"}]}]}

```

#### Security Issues

1. Improper Authentication/Authorization Checks
- This Docker Registry API is accessible without authentication. 
- A properly secured registry should return 401 when the "/v2/" endpoint is hit without credentials. 
- The response should include a WWW-Authenticate challenge, providing guidance on how to authenticate, such as with basic auth or a token service.


2. Shodan Dorks 
- Docker Private Registries

> "Docker-Distribution-Api-Version: registry" "200 OK" -gitlab

> https://www.shodan.io/search?query=%22Docker-Distribution-Api-Version%3A+registry%22+%22200+OK%22+-gitlab

3. Some Interesting Attack Reads
- https://book.hacktricks.xyz/pentesting/5000-pentesting-docker-registry



#### References & Good Reads

```
a. https://www.acunetix.com/vulnerabilities/web/docker-registry-api-is-accessible-without-authentication/
b. https://hackerone.com/reports/924487
c. https://blog.dixitaditya.com/exploiting-docker-registry/
d. https://notsosecure.com/anatomy-of-a-hack-docker-registry/
e. https://github.com/lothos612/shodan
```
