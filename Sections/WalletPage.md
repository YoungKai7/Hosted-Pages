Hosted Wallet Page
==================

The PayFabric hosted wallet page is used for embedding the wallet page into your application to allow your users to create or update their credit card / eCheck details (including billing address information).

Before embedding the wallet page, please ensure the following:

1. Generate a [Security Token](../../../../PayFabric-APIs/blob/master/Sections/Authentication.md#security-token).  Assume the token value is @TOKEN.
2. If updating, retrieve the unique card Id, see our [API documentation](../../../../PayFabric-APIs/blob/master/Sections/Wallets.md#retrieve-credit-cards--echecks) for how.  Assume the card Id is @CARDID.
 
Create a Credit Card / eCheck
-----------------------------

Build the hosted create wallet page URL this way:

https://sandbox.payfabric.com/V3/PayFabric/Web/Wallet/Create?customer={CUSTOMER_NUMBER}&tender={TENDER}&token={@TOKEN}
{TENDER} = *CreditCard* | *ECheck*

![Hosted create wallet page](https://s3-us-west-1.amazonaws.com/github-screenshot-repository/v2/HostedCreateWalletPage.png "Hosted create wallet page")


Update a Credit Card / eCheck
-----------------------------

Build the hosted update wallet page URL this way:

https://sandbox.payfabric.com/V3/PayFabric/Web/Wallet/edit?card={@CARDID}&token={@TOKEN}

![Hosted update wallet page](https://s3-us-west-1.amazonaws.com/github-screenshot-repository/v2/HostedEditWalletPage.png "Hosted update wallet page") 

Options
-------

PayFabric hosted wallet page accepts the below query string parameters to add options. You can use below query parameters by adding them to your hosted wallet page URL and connecting them with '&'.

>
| QueryString| Description | 
| :------------- | ------------- | 
|Country=&Street1=&Street2=&Street3=<br/>&City=&State=&Zip=&Email=&Phone= |This query string can pass initial billing address information|
|themename=|This parameter is to support 3rd party dynamically pass into theme name via query string. If the value is an existing theme name, then page will use this theme; If the value is an nonexistent theme name, then page will use the device default theme.|
|returnuri=|This parameter is to support 3rd party dynamically pass a return url via query string. If the value is a valid URL, then after the wallet is saved, page will redirect to the return url, and the unique Wallet ID will be appended to the return URL. |
