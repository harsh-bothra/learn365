# Salesforce Security Misconfiguration (Part-1)

Index | Section
--- | ---
**1** | [Scenario](#Scenario)
___

### Scenario
```
If you have encountered any Salesforce deployment to review and check for security best practices. Here are some of the things that you should check for:

1. Password Policy Best Practices
- Always check if a complex password policy is implemented. 
- Ensure that the Obscure secret answer for password resets is enabled. 
- Ensure that an effective lockout period is set. 
- Ensure that the maximum invalid login attempt is set to a smaller value.

2. Real-Time Event Monitoring
- Salesforce provides a way to keep a track of various events, activities, or anomalies that may occur such as Track anomalies in how users make API calls or Track when a user accesses data with list views and others.
- Ensure that all the necessary events are enabled for Real-Time Event Monitoring. 

3. Set Login IP Ranges 
- Ensure that the IP Ranges are configured from which a user can log in. This helps to enhance security from an outer perspective.

4. Enable Clickjacking Protection 
- Ensure that the clickjacking protection is enabled to ensure that it is not possible to iframe the sensitive pages and avoid attacks that may originate from clickjacking as a base. 
```
