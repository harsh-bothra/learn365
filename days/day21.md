# GraphQL Vulnerabilities (Part-2)

Index | Section
--- | ---
**1** | [Information Disclosure via Error Messages](#Information-Disclosure-via-Error-Messages)
**2** | [GraphQL Denial of Service](#GraphQL-Denial-of-Service)
**3** | [Insecure Direct Object Reference](#Insecure-Direct-Object-Reference)
**4** | [Good Burp Extensions ](#Good-Burp-Extensions)
**4** | [Labs ](#Labs)
**5** | [References](#References)
___

### Information Disclosure via Error Messages
```
- Similar to the normal information disclosure via error triggering. 
- Provide malformed or unexpected input within GraphQL queries.
- Sometimes you may observe verbose error messages revealing sensitive information.
```


### GraphQL Denial of Service
```
- Due to an improper limit on the maximum query depth, it might be possible to perform a denial of service in graphql implementation.
- Nest a query to unlimited depth and send this query on a GraphQL endpoint to observe anything suspicious.
- A good example: https://owasp-skf.gitbook.io/asvs-write-ups/kbid-285-graphql-dos
```

### Insecure Direct Object Reference
```
- Similar to normal API like IDORs
- A good example: https://owasp-skf.gitbook.io/asvs-write-ups/kbid-285-graphql-idor
```

### Good Burp Extensions 
```
- InQL 
- GraphQL Raider
```

### Labs

```
- https://github.com/dolevf/Damn-Vulnerable-GraphQL-Application
```

### References
- https://hackerone.com/reports/291721
- https://medium.com/bugbountywriteup/graphql-idor-leads-to-information-disclosure-175eb560170d
- https://owasp-skf.gitbook.io/asvs-write-ups/kbid-285-graphql-idor
