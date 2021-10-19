# Common Business Logic Issues (Part - 2)

Index | Section
--- | ---
**1** | [How to test](#How-to-test)
___

### How to Test
```
(cont'd...) 
5. Premium Feature Abuse 
- Try forcefully browsing the areas or some particular endpoints which come under premium accounts.
- Pay for a premium feature and cancel your subscription. If you get a refund but the feature is still usable, it's a monetary impact issue.
- Some applications use true-false request/response values to validate if a user is having access to premium features or not.
- Try using Burp's Match & Replace to see if you can replace these values whenever you browse the app & access the premium features.
- Always check cookies or local storage to see if any variable is checking if the user should have access to premium features or not.

6. Refund Feature Abuse
- Purchase a product (usually some subscription) and ask for a refund to see if the feature is still accessible.
- Try for currency arbitrage explained yesterday.
- Try making multiple requests for subscription cancellation (race conditions) to see if you can get multiple refunds.

7. Cart/Wishlist Abuse 
- Add a product in negative quantity with other products in positive quantity to balance the amount.
- Add a product in more than the available quantity.
- Try to see when you add a product to your wishlist and move it to a cart if it is possible to move it to some other user's cart or delete it from there.

8. Thread Comment Functionality
- Unlimited Comments on a thread
- Suppose a user can comment only once, try race conditions here to see if multiple comments are possible.
- Suppose there is an option: comment by the verified user (or some privileged user) try to tamper with various parameters in order to see if you can do this activity.
- Try posting comments impersonating some other users.
```

