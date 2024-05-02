# Wallet Management

The PayFabric hosted wallet pages are used for embedding the wallet page into your application to allow your users to create or update their card / eCheck details (including billing address information).

Refer to our [Wallet APIs](//https://github.com/PayFabric/APIs/blob/master/PayFabric/README.md#wallets--credit-cards--echecks) for full list of supported scenarios.

## Hosted Wallet Page Feature Comparison

Depending on business and integration requirements, PayFabric hosted wallet page can be embedded in multiple ways.

|Feature       | Responsive Hosted | Hosted |
|--------------| --------------|------------|
|Mobile Responsive| Supported  | Require custom CSS/JS     |
|Single Page UI Framework Support (React, Vue, etc.)| Seamless Integration | Requires Reloading Page| 
|Callback Support| Full Support| -----
|Customizability| CSS/JS| CSS/JS| 

## Responsive Hosted Wallet Page 

New version of the Hosted Wallet page has been designed and developed, With Responsive Wallet Hosted page, integrators will be able to create or update their PayFabric wallets on Mobile or tablet. 

Before embedding the hosted create wallet page, please ensure the following:

Below are the steps on how to embed Responsive Hosted Wallet page using PayFabric JavaScript SDK library:
 
1. [Generate]() JSON Web Token (JWT) 
2. [Initiate]() PayFabric JavaScript SDK library using the generated JWT.

Alternatively, Responsive Hosted Wallet page can be embedded through direct iFrame call. Refer to below:

* Set intent to 'ResponsiveCreate' or 'ResponsiveEdit'.
* Set token to the generated JWT.

Format: ``{baseUrl}/payment/web/wallet/{intent}?token={token}``

Example: ``https://sandbox.payfabric.com/payment/web/wallet/ResponsiveCreate?token={token}``



### Optional Parameters


PayFabric responsive hosted wallet page accepts the query string parameters below. Separate each parameter with ampersand ('&') to for the query string and add the query string to the hosted wallet page URL.

>
| QueryString| Description | 
| :------------- | :------------- | 
|Country=&Street1=&Street2=&Street3=<br/>&City=&State=&Zip=&Email=&Phone= |This query string can pass initial billing address information|
|ThemeName|This parameter is to support 3rd party dynamically passing into the theme name via query string. If the value is an existing theme name, then page will use this theme; If the value is a nonexistent theme name, then the page will use the device default theme.|
|UseBluefin|This parameter will take affect when [BlueFin Profile](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Bluefin.md) get enabled. When the value is '0', only regular keyboard entry for the credit card is available, when the value is `1`, only encryption key entry via Bluefin device for the credit card is available, when the value is `2`, both regular keyboard & encryption key entry for the credit card is available.|
|TrxInitiation|	This parameter specifies the wallet creation/updating initiated by the Merchant or Customer.|
|AcceptTender|This query string specifies the wallet tender when opening the responsive hosted create wallet page. Available values are 'CreditCard' and 'ECheck'.|

See [detailed guide](/sections/Responsive%20Hosted%20Wallet%20Page.md)

## Hosted Wallet Page

** Insert Overview

** Generate Security Token

** 

See [detailed guide](/sections/Hosted%20Wallet%20Page.md)



## 3D Secure Support

To enable the 3D Secure validation on hosted create wallet page, [Credit Card Validation](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/PayFabric%20Settings.md#transaction-options) setting must be enabled and the validation gateway must be EVO with eService processor.

<b>Note:</b> Hosted Create Wallet Page only supports 3D Secure 2.0, doesn't support 3D Secure 1.0.