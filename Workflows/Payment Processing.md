# Payment Processing

## Overview
PayFabric Hosted Payment Pages offers a robust and secure solution for processing payments online. PayFabric Hosted Payment Pages can be embedded into your application to allow for processing of transactions with credit cards and/or eCheck.

## Table of Contents

- [Payment Page Feature Comparison](#payment-page-feature-comparison)
- [Payment Processing Walkthrough](#payment-processing-walkthrough)
- [Alternative Payment Methods](#alternative-payment-methods)
- [3D Secure Support](#3d-secure-support)
- [Payment Terminal Signature Page](#payment-terminal-signature-page)

## Payment Page Feature Comparison

|Feature| RHPP (JS SDK)| HPP|
|-------| -------------| ---|
|Mobile Responsive | Supported|Require Custom CSS/JS |
|Alternative Payment Methods | Apple Pay, Google Pay, PayPal/Venmo | Not Supported |
|Save For Later Transaction |Not Supported|Supported |
|Payment Terminals| Not Supported  | PAX S300, D210, and PX7|
|Single Page UI Framework Support (React, Vue, etc.) | Seamless Integration | Requires Reloading Page |
|Callback Support | Full Support | ----- |
|BlueFin Support | Supported| Supported |
|Customizability | Custom CSS/JS |  Custom CSS/JS|

**** NOTE: 
**** Child RHPP iframe in RHPP SDK

## Payment Processing Walkthrough

This section will walk you through the essential steps to utilize Payfabric Hosted Payment Pages for secure payment processing inside your application. Before proceeding, review and use the appropriate base URL for when calling PayFabric APIs:

 Live Server:      ``https://www.payfabric.com/Payment/Web``

 Sandbox Server:   ``https://sandbox.payfabric.com/Payment/Web``

### Steps: 

1. **Generate a Security Token**

   Before initiating any payment transactions, you will need to generate a security token. This token will be passed into the Authorization header when creating new transactions through the PayFabric API. See [Security Token](../Sections/Security%20Token.md) for details on generating the token.

2. **Create a Transaction**

   Once you have obtained a security token, you can proceed to create a new transaction. This involves sending a request to PayFabric with relevant transaction details, such as the amount, currency, payment gateway, and transaction type. See the [Create a Transaction](https://github.com/PayFabric/APIs/blob/master/PayFabric/Sections/Transactions.md#create-a-transaction) API for details.

   Upon a succesful request, the API will return a transaction key that will be used for generating the hosted payment page.

3. **Load Payment Page**

   Once a transaction key is generated, you may now proceed to loading the hosted page. Depending on your requirements, you can choose between two options for the payment page:
   - **[Responsive Hosted Payment Page (RHPP)](../Sections/Responsive%20Hosted%20Payment%20Page%20(JavaScript%20SDK).md)**: For most use cases, use the Mobile Responsive Hosted Payment Page. This page can be embedded through both the PayFabric SDK as well as [through an iFrame](../Sections/Responsive%20Hosted%20Payment%20Page%20(iFrame).md).
   - **[Hosted Payment Page (HPP)](../Sections/Hosted%20Payment%20Page.md)**: For use cases where payment terminals are required, or when the transaction on the payment page should be saved to be processed at a later time, utilize this hosted payment page.

4. **Retrieve Response**

   After a payment is processed, results can be returned in different manners, mainly directly from PayFabric service through either the back-end (most secured) or the front-end (immediate response for user experience optimization). See [Retrieve Response](../Sections/Retrieve%20Response.md) for details.


## Alternative Payment Methods

The Responsive Hosted Payment Page (RHPP) support Alternative Payment Methods, such as Apple Pay, Google Pay, and Venmo/PayPal. Please check the detailed instructions for [Alternative Payment Methods](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/APM.md)

<b>Note:</b> 
1. Alternative payment methods are not available for transactions that have either surcharge or tip enabled.
2. If you are using an iFrame approach for Google Pay, then you must add `allow="payment"` attribute to your iframe.

## 3D Secure Support

3D Secure 2.0 is a protocol that was developed in compliance with the PSD2 (Payment Service Directive 2.0) mandate to make online payments more secure through advanced cardholder verification.

Only 3D Secure 2.0 is supported on Mobile Hosted Payment Page with the gateway as EVO and its the processor is EVO eService.

<b>Note:</b> 
1. 3D Secure is only supported through the Responsive Hosted Payment Page (RHPP). Hosted Payment Page (HPP) does NOT support 3DS.




