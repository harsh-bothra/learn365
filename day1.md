# 2FA Bypass Techniques

___
### Response Manipulation


>In response if "success":false \
Change it to "success":true

### Status Code Manipulation


>If Status Code is 4xx \
Try to change it to 200 OK and see if it bypass restrictions

### 2FA Code Leakage in Response


>Check the response of the 2FA Code Triggering Request to see if the code is leaked.

### JS File Analysis

> Rare but some JS Files may contain info about the 2FA Code, worth giving a shot

### 2FA Code Reusability

>Same code can be reused

### Lack of Brute-Force Protection

> Possible to brute-force any length 2FA Code

### Missing 2FA Code Integrity Validation

>Code for any user acc can be used to bypass the 2FA

### CSRF on 2FA Disabling

>No CSRF Protection on disabling 2FA, also there is no auth confirmation

### Password Reset Disable 2FA

>2FA gets disabled on password change/email change

### Backup Code Abuse

>Bypassing 2FA by abusing the Backup code feature. \
Use the above mentioned techniques to bypass Backup Code to remove/reset 2FA restrictions

### Clickjacking on 2FA Disabling Page

> Iframing the 2FA Disabling page and social engineering victim to disable the 2FA

### Enabling 2FA doesn't expire Previously active Sessions

>If the session is already hijacked and there is a session timeout vuln