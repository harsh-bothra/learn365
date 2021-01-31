# Password Reset Token Issues

Index | Section
--- | ---
**1** | [How to test](#How-to-test)
**2** | [References](#References)
___

### How to Test
```
1. Weak Cryptography in Password Reset Tokens 
- Always check randomness in password reset tokens. It is also a good idea to check password reset tokens against known schemes. 
Ref: https://medium.com/bugbountywriteup/weak-cryptography-in-password-reset-to-full-account-takeover-fc61c75b36b9

2. Reusable Password Reset Tokens 
- Use the token once and try to re-use it again. 
- Request a new token and try if the old one is still active. 
- Check how long a token stays alive. If it's >1 day and is reusable, you may report it.

3. IDOR (ATO)
- In the password reset link, assume there is something like this: https://harshbothra.tech/reset?token=sometoken&user=harsh
- try changing the value of the user parameter to the victim and see If the attack token can be used for resetting the victim's password. https://harshbothra.tech/reset?token=sometoken&user=victim

4. Lack of Random Generation in Password Reset Token
- Request multiple passwords reset tokens. 
- If all the requested tokens are identical, it is confirmed that some Identifier is crypted to generate a password reset token. 
- Try guessing the crypto else still an issue.

5. Weak/Small Password Reset Token is used 
- If a password reset token used by the application is weak/small/guessable, it can be brute-forced.

6. Password Reset Token not Validated 
- Navigate to the password reset link and remove the token parameter or send only empty values. 
- Only keep the user identifier and change that to the victim user's identifier 
- See if it is possible to change the password.

7. Excessive Information in JWT Based Password Reset Token 
- If the password reset token is JWT Based, check for the following: 
a. If there is any excessive info, it may contain an old password (never seen but you never know)
b. Make sure that asymmetric algo is used.

Some of the Broken Cryptography & Account Takeover Related methods are discussed in some of my talks, you can find them here: 
https://www.youtube.com/watch?v=mLi3qxhLIA0&list=PLYn5_MxRvV-fxPL90I-uebXQzQBXfIaY0&index=10
https://speakerdeck.com/harshbothra/broken-cryptography-and-account-takeovers
```

### References
- https://medium.com/bugbountywriteup/weak-cryptography-in-password-reset-to-full-account-takeover-fc61c75b36b9
- https://www.youtube.com/watch?v=mLi3qxhLIA0&list=PLYn5_MxRvV-fxPL90I-uebXQzQBXfIaY0&index=10
- https://speakerdeck.com/harshbothra/broken-cryptography-and-account-takeovers
