# Web Cache Deception Attack

This attack mainly happens when the Cache-Control directives are misconfigured and can be leveraged by an attacker to get hold of sensitive information.

Index | Section
--- | ---
**1** | [About the attack](#About-the-attack)
**2** | [Path confusion attacks](#Path-confusion-attacks)
**3** | [Cause](#cause)
**4** | [Scenario](#Scenario)
**5** | [How to test](#How-to-test)
___

### About the attack
```
- This attack requires User Interaction. 
- One of the important vectors is "Path Confusion Attack."
- Path Confusion Attack/Flexible URL Rewriting plays an important role in this Attack
```

### Path confusion attacks
```
- Many Web Applications have URL Rewriting Rules.
- In such scenarios depending upon the configuration of the webserver, both of these URLs will be considered as (http://harshbothra.tech/myprofile).
- http://harshbothra.tech/myprofile
- http://harshbothra.tech/myprofile/test.css
```

### Cause
```
- The following example code uses a regex that will consider both of the above examples as the same treaty: 

from django.conf.urls import url

patterns = [url(r'^myprofile/', ...)]
```

### Scenario
```
- Now, when the user requests for a static resource such as CSS, JPG, JS, etc., the web cache will consider to cache it considering it as static content (Expected Behavior) and this is where the web cache deception attack will come into the picture.
```

### How to Test
```
1. Navigate to an application and look for a page that may contain sensitive information such as http://harshbothra.tech/myprofile
2. Now add any static file after /myprofile such as test.css, test.jpg, etc. For Ex: http://harshbothra.tech/myprofile/test.jpg
3. Now, if the app displays the same /myprofile page, it might be cached. 
4. Now, From another session (where this user is not logged in), navigate to the same URL: http://harshbothra.tech/myprofile/test.jpg
5. If you can see the information about the victim user. The attack is successful.
```
