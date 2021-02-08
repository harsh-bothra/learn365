#  OpenID Connect Implementation Issues
Index | Section
--- | ---
**1** | Introduction
**2** | Attack Vectors
**3** | Side Notes

___


#### Introduction
```
1. OIDC (Open ID Connect) is an authentication layer on top of OAuth 2.0, an authorization framework. The standard is controlled by the OpenID Foundation. 
2. More Information: https://openid.net/connect/
3. Today's learning is referenced from: https://security.lauritz-holtmann.de/post/sso-security-overview/

```

#### Attack Vectors
```
1. Login Confusion Attack

- Detailed Read: https://security.lauritz-holtmann.de/post/sso-security-login-confusion/

2. Injection of CRLF Sequences

- Detailed Read: https://security.lauritz-holtmann.de/post/sso-security-crlf-injection/

3. Server-Side Request Forgery

- Detailed Read: https://security.lauritz-holtmann.de/post/sso-security-ssrf/

4. Redirect URI Schemes

- Detailed Read: https://security.lauritz-holtmann.de/post/sso-security-redirect-uri/


5. Reusable State Parameter

- Detailed Read: https://security.lauritz-holtmann.de/post/sso-security-state/

```

#### Side Notes

```
a. This is a really nice article and fun read to understand about the implementation and issues. Kudos to the researcher.
b. Original Tweet: https://twitter.com/_lauritz_/status/1322242562216890369

```