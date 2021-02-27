#  JSON Interoperability Vulnerabilities
Index | Section
--- | ---
**1** | Introduction
**2** | Potential Test Cases
**3** | Labs 
**4** | References 

___


#### Introduction
```
1. Recently BishopFox Labs released a research blog on the JSON Interoperability Vulnerabilities explaining multiple security issues that may exists in the JSON based schemas. 
2. The same JSON document can be parsed with different values across microservices, leading to a variety of potential security risks.

```

#### Potential Test Cases
```
1. Inconsistent Duplicate Key Precedence

2. Key Collision: Character truncation and Comments

3. JSON Serialization Quirks

4. Float and Integer Representation

5. Permissive Parsing and Other Bugs
```

#### Labs

```
a. https://github.com/BishopFox/json-interop-vuln-labs

```

#### References 

```
a. https://labs.bishopfox.com/tech-blog/an-exploration-of-json-interoperability-vulnerabilities

```

#### Note: This work is carried out by BishopFox Labs & this repository doesn't take any credit for the same. Shoutout to @theBumbleSec for sharing this research work.