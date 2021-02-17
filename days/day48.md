# Incomplete Trailing Escape Pattern Issue
Index | Section
--- | ---
**1** | Introduction
**2** | How to Test
**3** | References & Good Reads

___


#### Introduction
```
- Missing Input Validation is the root cause for tons of security vulnerability.
- Recently, I have encountered an interesting scenario where due to missing sanitization in Incomplete Trailing Escape Patterns, I was able to perform a simple Availability (DoS like) impact on the application. 
- There are many escape sequence, the one I encountered was `%` where due to missing sequence after %, I was able to confuse the library parsing the result into throwing error leading to the availability impact. 

```

#### How to Test
```
1. Let's assume the application has a "First Name" option which is stored in the backend to some DB.
2. Now, I injected some incomplete sequences such as !@#$%^ into the first name field and application successfully saved this input.
3. Assume there's an API which specifically allows to fetch first name for all the users.
4. Now, due to the Incomplete Trailing Escape Patterns, the GET API was not able to parse the data properly and throwed Internal Server Error.
5. Since this was a shared API, all the users were impacted. 


This is one of the recently encountered scenario, there may be other impact of this as well. 


```


#### References & Good Reads 

```
a. https://www.programmersought.com/article/1312520870/

```