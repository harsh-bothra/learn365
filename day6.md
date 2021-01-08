#  Cross-Site Leaks (XS-Leaks)
Index | Section
--- | ---
**1** | What is Cross-Site Leaks
**2** | Cross-Site Oracle
**3** | A Simple Example
**4** | Attacks using XS-Leaks
**5** | XS-Search Exploitation Workflow
**6** | References
___
#### What is Cross-Site Leaks
```
1. Cross-Site Leaks/XS-Leaks is a less explored security issue that usually comes from Side-Channel Attacks. 

2. This basically utilizes the web's core principle of composability in order to determine & extract useful information. 

3. XS-Leaks take advantage of small pieces of information which are exposed during interactions between websites.

```

#### Cross-Site Oracle
```
1. This can be considered as a querying mechanism. The information used for this attack is of binary form and called Oracles. They usually have an answer of "Yes" or "No". You can say True or False. 

2. For Example: Does User Harsh Exists in the Application. Yes, means that the user is there in the application. 

3. An attacker requires to smartly form queries in order to successfully execute this attack and gain hold of sensitive information.

```

#### A Simple Example 
```

1. Suppose that bank.com has an API endpoint that returns data about a user’s receipt for a given type of transaction.

2. evil.com can attempt to load the URL bank.com/my_receipt?q=groceries as a script. By default, the browser attaches cookies when loading resources, so the request to bank.com will carry the user’s credentials.

3. If the user has recently bought groceries, the script loads successfully with an HTTP 200 status code. If the user hasn’t bought groceries, the request fails to load with an HTTP 404 status code, which triggers an Error Event.

4. By listening to the error event and repeating this approach with different queries, the attacker can infer a significant amount of information about the user’s transaction history.

```

#### Attacks using XS-Leaks

```
1. XS-Search: An attacker try to abuse the query mechanism such as search functionality to leak and get hold of user's inforamtion.

2. Error Events: Based on the Error Message returned by the application, it may be possible to enumerate sensitive information. This is similar to user enumeration techniques.

3. Frame Counting: window.length which provides the number of frames in the window. This attribute can provide valuable information about a page to an attacker.

4. Navigation Attacks: To detect if any kind of navigation occurred in order to know specific information about the victim. 

5.  Cache Probing: Workes based on detecting whether the web page was cached or not.

6. ID Attribute

7. Post Message Broadcasts

8. Abusing Browser Features Abusing Browser Features 
    - CORB (Cross-Origin Read Blocking)
    - CORP (Cross-Origin Resource Policy)

9. Timing Attacks
    - Clock Based 
    - Network Timing
    - Execution Timing
    - Hybrid Timing 
    - Connection Pool
```


#### XS-Search Exploitation Workflow
```
1.Define a timeline when there is a Hit (Success) vs There is a Failure (Miss)
2. Start attacking the Querying Endpoint. 
3. For Example: ?search=h (Throws a Hit)
search for the next word appended to `h` i.e. ?search=ha otherwise change the word i.e. ?search=b
4. By this you can try to extract the complete info it that exist.

```

#### References

```
a. https://xsleaks.com/
b. https://arxiv.org/pdf/1908.02204.pdf
c. https://github.com/xsleaks/xsleaks/wiki/Browser-Side-Channels
d. http://sirdarckcat.blogspot.com/2019/03/http-cache-cross-site-leaks.html
e. https://polict.net/blog/web-tracking-via-http-cache-xs-leaks/
f. https://hackerone.com/reports/723175
g. https://xsleaks.dev/category/attack/
h. https://owasp.org/www-community/attacks/Cross_Site_History_Manipulation_(XSHM)
i. https://portswigger.net/research/xs-leak-leaking-ids-using-focus
j. https://sirdarckcat.blogspot.com/2019/03/http-cache-cross-site-leaks.html
k. https://medium.com/@terjanq/massive-xs-search-over-multiple-google-products-416e50dd2ec6
l. https://owasp.org/www-pdf-archive/AppSecIL2015_Cross-Site-Search-Attacks_HemiLeibowitz.pdf
m. Reference: https://hackerone.com/reports/505424
n. https://www.imperva.com/blog/facebook-privacy-bug/
o. https://hackerone.com/reports/491473

```
