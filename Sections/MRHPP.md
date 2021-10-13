Mobile Hosted Payment Page
==========================
A new version of the Hosted Payment page has been designed and developed, to be more streamlined and intended for a shopping cart/checkout experience, it will be only obtaining the minimum required information and no other elements aside from Payment Information, Billing Information will be able to be input into the form.  All other fields such as Transaction Type, Gateway Profile, Transaction amount etc must be set during the initial Create Transaction API call.

Before embedding the payment page, please ensure the following:

1. Generate a new transaction, see our [API documentation](../../../../PayFabric-APIs/blob/master/PayFabric/Sections/Transactions.md#create-a-transaction) for how. 
2. Generate a [JWT token](../../../../PayFabric-APIs/blob/master/PayFabric/Sections/JWTToken.md) with the transaction key.  Assume the token value is @TOKEN.

Build the payment hosted page URL this way:

https://sandbox.payfabric.com/Payment/Web/Transaction/ResponsiveProcess?token={@TOKEN}
 
![MobileHostedPaymentPageNoSurcharge](https://raw.githubusercontent.com/PayFabric/Portal/master/PayFabric/Sections/Screenshots/MobileHostedPaymentPageNoSurcharge.png "MobileHostedPaymentPageNoSurcharge") 

Options
-------

PayFabric mobile hosted payment page accepts the below query string parameters to add options. You can use below query parameters by adding them to your mobile hosted payment page URL and connecting them with '&'.

>
| QueryString| Description | 
| :------------- | ------------- | 
|ThemeName|This parameter is for supporting 3rd party dynamically pass into theme name via query string. If the value is an existing theme name, then page will use this theme; If the value is an nonexistent theme name, then page will use the device default theme.|
|UseBluefin|This parameter will take affect when [BlueFin Profile](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Bluefin.md) get enabled. When the value is '0', only regular keyboard entry for credit card is available, when the value is `1`, only encryption key entry via Bluefin device for credit card is available, when the value is `2`, both regular keyboard & encryption key entry for credit card is available.|
|Accepttender|This parameter is to specify the accepted payment methods, the list of methods is: CreditCard, ECheck and PayPal, If accept multiple payment methods, then seperate the methods with ','.|
|UseDefaultWallet|When the value is `0`, then the default wallet won't load out while open hosted payment page. And if you set the value as `1`, then PayFabric will load the default wallet on hosted payment page by default.  Default value is `1`.|


Mobile Hosted Payment Page with Surcharge
===================================
PayFabric provides the ability for merchants to support surcharge on Mobile Hosted Payment page in order to pass on processing cost to the end customers for EVO gateway.
Only when customer is using credit card, PayFabric will shows the surcharge rate and surcharge amount on Mobile Hosted Payment page.

Surcharge amount = (Transaction amount + Tip amount) x Surcharge percentage

![Mobile Hosted payment page With Surcharge Tip](https://raw.githubusercontent.com/PayFabric/Portal/master/PayFabric/Sections/Screenshots/MobileHostedPaymentPageWithSurchargeTip.png "Mobile Hosted payment page With Surcharge Tip")


Mobile Hosted Payment Page with Tip 
===================================
PayFabric provides the ability for merchants to support Tip on Mobile Hosted Payment page for eCommerce customer. To enable Tip, please refer the [PayFabric Settings](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/PayFabric%20Settings.md#transaction-options)

![Mobile Hosted payment page With Tip](https://raw.githubusercontent.com/PayFabric/Portal/master/PayFabric/Sections/Screenshots/MobileHostedPaymentPageWithTip.png "Mobile Hosted payment page With Tip")

Support Alternative Payment Methods with MRHPP
================================
Please check the detailed instructions for [Alternative Payment Methods](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/APM.md)

<b>Note:</b> Alternative payment methods are not available for the transaction enable surcharge or enabled tip.

Mobile Hosted Payment Page 3D Secure support
======================================
3D Secure 2.0 is a protocol that was developed in compliance with the PSD2 (Payment Service Directive 2.0) mandate to make online payments more secure through advanced cardholder verification. 

Both 3D Secure 1.0 and 3D Secure 2.0 are supported on Mobile Hosted Payment Page with the gateway as EVO and its the processor is EVO eService.

