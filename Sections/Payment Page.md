Hosted Payment Page
===================

The PayFabric hosted payment page is used for embedding the payment page into your application to allow your users to process a transaction.

Before embedding the payment page, please ensure the following:

1. Generate a [Security Token](/Sections/Security%20Token.md).  Assume the token value is @TOKEN.
2. Generate a new transaction, see our [API documentation](../../../../PayFabric-APIs/blob/master/PayFabric/Sections/Transactions.md#create-a-transaction) for how.  Assume the transaction key is @TRXKEY.
 
Build the payment hosted page URL this way:

https://sandbox.payfabric.com/Payment/Web/Transaction/Process?key={@TRXKEY}&token={@TOKEN}

![Hosted payment page](https://raw.githubusercontent.com/PayFabric/Portal/master/PayFabric/Sections/Screenshots/HostedPaymentPage.png "Hosted payment page") 

Hosted Payment Page with Surcharge
===================================
PayFabric provide the ability for merchants to support surcharge in order to pass on their processing cost to the end customers for EVO gateway.
1. PayFabric’s hosted payment page added 3 additional fields to support surcharge: Surcharge Rate, Surcharge Amount and Final Amount. 
2. By default, these fields are hidden and will only available if surcharge rate is enabled on gateway profile setting for the in-used gateway profile. Surcharge Amount, Surcharge Rate and Final Amount will be read-only as they’re calculated fields by PayFabric based on the provided rate. 
3. It’s up to 3rd party application to design and structure these 3 fields using CSS/JS to make it fits on your application’s UI and UX. 
![HostedPaymentPageWithSurcharge](https://raw.githubusercontent.com/PayFabric/Portal/master/PayFabric/Sections/Screenshots/HostedPaymentPageWithSurcharge.png "HostedPaymentPageWithSurcharge") 


Options
-------

PayFabric hosted payment page accepts the below query string parameters to add options. You can use below query parameters by adding them to your hosted payment page URL and connecting them with '&'.

>
| QueryString| Description | 
| :------------- | ------------- | 
|Country=&Street1=&Street2=&Street3=<br/>&City=&State=&Zip=&Email=&Phone= |This query string can pass initial billing address information, this query string only works on the hosted payment page when there is no selected wallet record.|
|UseDefaultWallet|When the value is `0`, then the default wallet won't load out while open hosted payment page. And if you set the value as `1`, then PayFabric will load the default wallet on hosted payment page by default.  Default value is `1`.|
|TempSave|When the value is `1`, then user can only save the transaction on hosted payment page.  Default value is `0`.|
|CardSwipe|When the value is `true`, then PayFabric will start processing the transaction automatically once user swipe the card. But still user can enter card info manually by click Cancel button on the pop up card swipe message box. Default value is `false`.|
|ThemeName|This parameter is to support 3rd party dynamically pass into theme name via query string. If the value is an existing theme name, then page will use this theme; If the value is an nonexistent theme name, then page will use the device default theme.|
|ReturnUri|	This parameter is to support 3rd party dynamically pass a return url via query string. If the value is a valid URL, then after the transaction is processed, the page will redirect to the return url, and the transaction response fields will be appended to the return URL as parameters.|
|isusenewtheme|	When the value is `1`, PayFabric's hosted page URL will trigger the V3 layout instead of V2 Layout. Default value is `0`|
|ProcessingMethod|This parameter will take affect when [Payment Terminals](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Payment%20Terminals.md) get enabled. Allow 3rd party application to enable/disable EMV on-the-fly on a per-transaction basis via the following query string parameter. `ProcessingMethod = 0: Web Entry only, ProcessingMethod = 1: EMV only, ProcessingMethod = 2: Both Web Entry and EMV`|
|UseBluefin|This parameter will take affect when [BlueFin Profile](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Bluefin.md) get enabled. When the value is '0', only regular keyboard entry for credit card is available, when the value is `1`, only encryption key entry via Bluefin device for credit card is available, when the value is `2`, both regular keyboard & encryption key entry for credit card is available.|
|useshipping|	When the value is `1`, PayFabric's checkout hosted page URL will load history shipping addresses. When the value is '0', PayFabric's chekcout hosted page will NOT load history shipping addresses. Default value is `1`|
|AuthorizationType| The authorization type of the transaction, valid values are ``Reauthorization``, ``Resubmission``, ``Incremental`` or ``NotSet``|
|TrxSchedule| The type authorization of transaction to be processed, valid values are ``Unscheduled``, ``ScheduledInstallment``, ``ScheduledRecurring`` or ``NotSet``|
|TrxInitiation| The entity that initiated the transaction, valid values are ``Merchant``, ``Customer`` or ``NotSet``| 
