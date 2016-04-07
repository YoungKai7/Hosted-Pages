Hosted Payment Page
===================

The PayFabric hosted payment page is used for embedding the payment page into your application to allow your users to process a transaction.

Before embedding the payment page, please ensure the following:

1. Generate a [Security Token](../../../../PayFabric-APIs/blob/master/Sections/Authentication.md#security-token).  Assume the token value is @TOKEN.
2. Generate a new transaction, see our [API documentation](../../../../PayFabric-APIs/blob/master/Sections/Transactions.md#create-a-transaction) for how.  Assume the transaction key is @TRXKEY.
 
Build the payment hosted page URL this way:

https://sandbox.payfabric.com/V3/PayFabric/Web/Transaction/Process?key={@TRXKEY}&token={@TOKEN}

![Hosted payment page](https://s3-us-west-1.amazonaws.com/github-screenshot-repository/v2/HostedPaymentPage.png "Hosted payment page") 

Options
-------

PayFabric hosted payment page accepts the below query string parameters to add options. You can use below query parameters by adding them to your hosted payment page URL and connecting them with '&'.

>
| QueryString| Description | 
| :------------- | ------------- | 
|Country=&Street1=&Street2=&Street3=<br/>&City=&State=&Zip=&Email=&Phone= |This query string can pass initial billing address information, this query string only works on the hosted payment page when there is no selected wallet record.|
|UseDefaultWallet=1|When the value is `0`, then the default wallet won't load out while open hosted payment page. And if you set the value as `1`, then PayFabric will load the default wallet on hosted payment page by default.  Default value is `1`.|
|TempSave=0|When the value is `1`, then user can only save the transaction on hosted payment page.  Default value is `0`.|
|CardSwipe=false|When the value is `true`, then PayFabric will start processing the transaction automatically once user swipe the card. But still user can enter card info manually by click Cancel button on the pop up card swipe message box. Default value is `false`.|
|ThemeName=|This parameter is to support 3rd party dynamically pass into theme name via query string. If the value is an existing theme name, then page will use this theme; If the value is an nonexistent theme name, then page will use the device default theme.|
|ReturnUri=|	This parameter is to support 3rd party dynamically pass a return url via query string. If the value is a valid URL, then after the transaction is processed, the page will redirect to the return url, and the transaction response fields will be appended to the return URL as parameters.|
