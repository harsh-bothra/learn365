# Common Business Logic Issues: Part-1

Index | Section
--- | ---
**1** | [How to test](#How-to-test)
___

### How to Test
```
1. Review Functionality
- Some applications have an option where verified reviews are marked with some tick or it's mentioned. Try to see if you can post a review as a Verified Reviewer without purchasing that product.
- Some app provides you with an option to provide a rating on a scale of 1 to 5, try to go beyond/below the scale-like provide 0 or 6 or -ve.
- Try to see if the same user can post multiple ratings for a product. This is an interesting endpoint to check for Race Conditions.
- Try to see if the file upload field is allowing any exts, it's often observed that the devs miss out on implementing protections on such endpoints. 
- Try to post reviews like some other users.
- Try performing CSRF on this functionality, often is not protected by tokens

2. Coupon Code Functionality 
- Apply the same code more than once to see if the coupon code is reusable. 
- If the coupon code is uniquely usable, try testing for Race Condition on this function by using the same code for two accounts at a parallel time.
- Try Mass Assignment or HTTP Parameter Pollution to see if you can add multiple coupon codes while the application only accepts one code from the Client Side. 
- Try performing attacks that are caused by missing input sanitization such as XSS, SQLi, etc. on this field
- Try adding discount codes on the products which are not covered under discounted items by tampering with the request on the server-side. 

3. Delivery Charges Abuse 
- Try tampering with the delivery charge rates to -ve values to see if the final amount can be reduced.
- Try checking for the free delivery by tampering with the params.

4. Currency Arbitrage 
- Pay in 1 currency say USD and try to get a refund in EUR. Due to the diff in conversion rates, it might be possible to gain more amount.
```
