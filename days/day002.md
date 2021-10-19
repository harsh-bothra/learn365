#  Regular Expression Denial of Service

Index | Section
--- | ---
**1** | What is ReDos
**2** | Method
**3** | Evaluation
**4** | Resources
**5** | Prevention
**6** | References

___
#### What is ReDos
```
Due to weakly implemented RegEx Sometimes it is possible to perform a DoS attack by making this expression to evaluate an expression which will make the application work relatively slow.

Usually this attack is explored and exploited when the source code is available and you can figure out what regular expressions are used in the code at what fields. 

For example, at the mobile no input field, what is the regex that validates the mobile no input field.
However, you can also try to find this in Black/Gray Box engagements. 
```

#### Method

```
Open the JavaScript files and search for the "RegExp(" function and try to figure out what function utilize that particular Regex.
```
#### Evaluation
```
https://github.com/2bdenny/ReScue 

This is a good tool to evaluate and identify if the given regex is vulnerable or not. 
This tool will also provide a string that will make the vulnerable RegEx go into potential ReDoS Attacks.

It is important to understand how RegEx works and not only with ReDoS attack but it is useful overall.
```
#### Resources
```
Some of the good websites to learn about Regex are

https://rexegg.com
https://regexone.com
https://speakerdeck.com/harshbothra/having-fun-with-regex
https://javascript.info/regexp-catastrophic-backtracking
```
#### Prevention
```
https://regular-expressions.info/redos.html 
```
#### References
```
https://hackerone.com/reports/511381
https://hackerone.com/reports/661722
```
