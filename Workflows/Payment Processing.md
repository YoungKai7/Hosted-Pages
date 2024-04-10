# Payment Processing

** insert table of contents

** insert overview

## Payment Page Feature Comparison

|Feature| RHPP (JS SDK)| HPP|
|-------| -------------| ---|
|Mobile Responsive | Supporte d|Require Custom CSS/JS |
|Alternative Payment Methods | Apple Pay, Google Pay, PayPal/Venmo | Not Supported |
|Save For Later Transaction |Not Supported|Supported |
|Payment Terminals| Not Supported  | PAX S300, D210, and PX7|
|Single Page UI Framework Support (React, Vue, etc.) | Seamless Integration | Requires Reloading Page |
|Callback Support | Full Support | ----- |
|BlueFin Support | Supported| Supported |
|Customizability | Custom CSS/JS |  Custom CSS/JS|


**** NOTE: 
**** Child RHPP iframe in RHPP SDK

## Hosted Payment Page

** Overview Intro

** Generate Security Token

** Generate New Transaction

** Payment Page Link (Mobile Responsive)

** Payment Page Link (include terminal entry and sig)

** Retrieve Response


## Alternative Payment Methods

Please check the detailed instructions for [Alternative Payment Methods](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/APM.md)

<b>Note:</b> 
1. Alternative payment methods are not available for the transaction enable surcharge or enabled tip.
2. Additionally, if you are using an iFrame approach for Google Pay, then you must add `allow="payment"` attribute to your iframe.

## 3D Secure Support

3D Secure 2.0 is a protocol that was developed in compliance with the PSD2 (Payment Service Directive 2.0) mandate to make online payments more secure through advanced cardholder verification.

Only 3D Secure 2.0 is supported on Mobile Hosted Payment Page with the gateway as EVO and its the processor is EVO eService.




