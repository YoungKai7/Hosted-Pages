Mobile Hosted Payment Page
==========================
A new version of the Hosted Payment page has been designed and developed, to be more streamlined and intended for a shopping cart/checkout experience, it will be only obtaining the minimum required information and no other elements aside from Payment Information, Billing Information will be able to be input into the form.  All other fields such as Transaction Type, Gateway Profile, Transaction amount etc must be set during the initial Create Transaction API call.

Before embedding the payment page, please ensure the following:

1. Generate a new transaction, see our [API documentation](../../../../PayFabric-APIs/blob/master/PayFabric/Sections/Transactions.md#create-a-transaction) for how. 
2. Generate a [JWT](/Sections/jwttoken.md) with the transaction key.  Assume the token value is @TOKEN.

Build the payment hosted page URL this way:

https://sandbox.payfabric.com/Payment/Web/Transaction/ResponsiveProcess?token={@TOKEN}
 
![MobileHostedPaymentPageNoSurcharge](https://raw.githubusercontent.com/PayFabric/Portal/master/PayFabric/Sections/Screenshots/MobileHostedPaymentPageNoSurcharge.png "MobileHostedPaymentPageNoSurcharge") 

Mobile Hosted Payment Page with Surcharge
===================================
PayFabric provide the ability for merchants to support surcharge in order to pass on their processing cost to the end customers for EVO gateway.
1. PayFabric’s mobile hosted payment page supports surcharge
2. By default, surcharge info are hidden and will only available if surcharge rate is enabled on gateway profile setting for the in-used gateway profile. Surcharge Amount, Surcharge Rate and Final Amount will be read-only as they’re calculated fields by PayFabric based on the provided rate. 
3. It’s up to 3rd party application to design and structure these 3 fields using CSS/JS to make it fits on your application’s UI and UX. 

![Mobile Hosted payment page](https://raw.githubusercontent.com/PayFabric/Portal/master/PayFabric/Sections/Screenshots/MobileHostedPaymentPage.png "Mobile Hosted payment page")

Options
-------

PayFabric mobile hosted payment page accepts the below query string parameters to add options. You can use below query parameters by adding them to your mobile hosted payment page URL and connecting them with '&'.

>
| QueryString| Description | 
| :------------- | ------------- | 
|UseDefaultWallet|When the value is `0`, then the default wallet won't load out while open mobile hosted payment page. And if you set the value as `1`, then PayFabric will load the default wallet on hosted payment page by default.  Default value is `1`.|
|ThemeName|This parameter is to support 3rd party dynamically pass into theme name via query string. If the value is an existing theme name, then page will use this theme; If the value is an nonexistent theme name, then page will use the device default theme.|
|UseBluefin|This parameter will take affect when [BlueFin Profile](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Bluefin.md) get enabled. When the value is '0', only regular keyboard entry for credit card is available, when the value is `1`, only encryption key entry via Bluefin device for credit card is available, when the value is `2`, both regular keyboard & encryption key entry for credit card is available.|
