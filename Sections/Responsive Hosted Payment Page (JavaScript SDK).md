# Responsive Hosted Payment Page

PayFabric provides a JavaScript library to support both processing and saving credit card and eCheck information. The PayFabric JS SDK offers a mobile-friendly payment page that can be embedded into your application through a pop-up window or element.

Alternatively, an iFrame can be used to embed the Responsive Hosted Payment Page. See [RHPP (iFrame)](../Sections/Responsive%20Hosted%20Payment%20Page%20(iFrame).md) for details.

## Walkthrough

This section will walk you through how to embed the Responsive Hosted Payment Page into your application for secure payment processing. 

**Before proceeding**, you will need to first generate a security token and then a transaction key. See [Payment Processing Walkthrough](../Workflows/Payment%20Processing.md#Payment-Processing-Walkthrough) for details.

Once a transaction key is generated, follow the steps below to utilize the payment page:
### Steps: 

1. **Generate a JWT Token**

   Call the [Generate Token for Payment Processing](../Sections/JWTToken.md#generate-token-for-payment-processing) API to generate a JWT Token.

2. **Load Payment Page**

   Once you have retrieved the JWT token from the response body, the Responsive Hosted Payment Page can now be loaded. Please read [this section](../JavaScript%20SDK/JavaScript-SDK.md#Initiate-JavaScript-SDK-Library) on how to initiate the JavaScript SDK Library.
   - View the [SDK Options](../JavaScript%20SDK/JavaScript-SDK.md#SDK-Options) section to see a list of settings and options that can be passed into the `payfabricpaymentssdk` object. These options can be used to modify the behavior of the payment page.

3. **Retrieve Response**

    See [Retrieve Response](../Sections/Retrieve%20Response.md) for details on receiving the transaction response from PayFabric.

## Alternative Payment Methods

The Responsive Hosted Payment Page (RHPP) support Alternative Payment Methods, such as Apple Pay, Google Pay, and Venmo/PayPal. Please check the detailed instructions for [Alternative Payment Methods](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/APM.md)

<b>Note:</b> 
1. Alternative payment methods are not available for transactions that have either surcharge or tip enabled.
2. If you are using an iFrame approach for Google Pay, then you must add `allow="payment"` attribute to your iframe.

## 3D Secure Support

3D Secure 2.0 is a protocol that was developed in compliance with the PSD2 (Payment Service Directive 2.0) mandate to make online payments more secure through advanced cardholder verification.

Only 3D Secure 2.0 is supported on Mobile Hosted Payment Page with the gateway as EVO and its the processor is EVO eService.

<b>Note:</b> 
1. 3D Secure is only supported through the Responsive Hosted Payment Page (RHPP) **with the EVO processor**. Hosted Payment Page (HPP) does NOT support 3DS.
