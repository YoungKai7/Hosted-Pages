Responsive Hosted Wallet Page  
====================================
A new version of the Hosted Wallet page has been designed and developed, With this Mobile Responsive Wallet Hosted page, the integrator will be able to create or update their PayFabric wallets on Mobile or tablet. 

Create a Credit Card / eCheck
-----------------
Before embedding the hosted create wallet page, please ensure the following:

1. Generate a [JWT token](../../../../PayFabric-APIs/blob/master/PayFabric/Sections/JWTToken.md) with the @CustomerName.  Assume the token value is @TOKEN.

Build the Hosted Create Wallet Page URL this way:

https://sandbox.payfabric.com/payment/web/wallet/ResponsiveCreate?token={@TOKEN}
![MRHCWP](https://github.com/PayFabric/Hosted-Pages/blob/master/Sections/MRHCWP.png "MRHCWP")


Edit a Credit Card / eCheck   
------------------------
Before embedding the hosted edit wallet page, please ensure the following:

1. Retrieve the unique card Id, see our [API documentation](../../../../PayFabric-APIs/blob/master/PayFabric/Sections/Wallets.md#retrieve-credit-cards--echecks) for how.  Assume the card Id is @CARDID.
2. Generate a [JWT token](../../../../PayFabric-APIs/blob/master/PayFabric/Sections/JWTToken.md) with the @ID.  Assume the token value is @TOKEN.

Build the Hosted Edit Wallet Page URL this way:

https://sandbox.payfabric.com/payment/web/wallet/ResponsiveEdit?token={@TOKEN}

![MRHEWP](https://github.com/PayFabric/Hosted-Pages/blob/master/Sections/MRHEWP.png "MRHEWP")

Optional Parameters
-------

PayFabric hosted wallet page accepts the query string parameters below. Separate each parameter with ampersand ('&') to for the query string and add the query string to the hosted wallet page URL.

>
| QueryString| Description | 
| :------------- | :------------- | 
|Country=&Street1=&Street2=&Street3=<br/>&City=&State=&Zip=&Email=&Phone= |This query string can pass initial billing address information|
|ThemeName|This parameter is to support 3rd party dynamically passing into the theme name via query string. If the value is an existing theme name, then page will use this theme; If the value is a nonexistent theme name, then the page will use the device default theme.|
|UseBluefin|This parameter will take affect when [BlueFin Profile](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Bluefin.md) get enabled. When the value is '0', only regular keyboard entry for the credit card is available, when the value is `1`, only encryption key entry via Bluefin device for the credit card is available, when the value is `2`, both regular keyboard & encryption key entry for the credit card is available.|
|TrxInitiation|	This parameter specifies the wallet creation/updating initiated by the Merchant or Customer.|
|AcceptTender|This query string specifies the wallet tender when opening the responsive hosted create wallet page. Available values are 'CreditCard' and 'ECheck'.|
