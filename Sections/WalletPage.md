Hosted Wallet Page
==================

The PayFabric hosted wallet page is used for embedding the wallet page into your application to allow your users to create or update their credit card / eCheck details (including billing address information).

Before embedding the wallet page, please ensure the following:

1. Generate a [Security Token](https://github.com/PayFabric/APIs/blob/v2/Sections/Transactions.md#security-token).  Assume the token value is @token.
2. If updating, retrieve the unique card Id, see our [API documentation](https://github.com/PayFabric/APIs/blob/v2/Sections/Wallets.md#retrieve-credit-cards--echecks) for how.  Assume the card Id is @cardID.
 
Create a Credit Card / eCheck
-----------------------------

Build the hosted create wallet page URL this way:

https://sandbox.payfabric.com/V2/Web/Wallet/Create?customer=AARONFIT0001&tender=CreditCard&token=@token
tender = *CreditCard* | *ECheck*

![Hosted create wallet page](https://s3-us-west-1.amazonaws.com/github-screenshot-repository/v2/HostedCreateWalletPage.png "Hosted create wallet page")


Update a Credit Card / eCheck
-----------------------------

Build the hosted update wallet page URL this way:

https://sandbox.payfabric.com/V2/Web/Wallet/edit?card=@cardID&token=@token

![Hosted update wallet page](https://s3-us-west-1.amazonaws.com/github-screenshot-repository/v2/HostedEditWalletPage.png "Hosted update wallet page") 

Options
-------

PayFabric hosted wallet page accepts the below query string parameters to add options. You can use below query parameters by adding them to your hosted wallet page URL and connecting them with '&'.

>
| QueryString| Description | 
| :------------- | ------------- | 
|Country=&Street1=&Street2=&Street3=<br/>&City=&State=&Zip=&Email=&Phone= |This query string can pass initial billing address information|
|themename=|This parameter is to support 3rd party dynamically pass into theme name via query string. If the value is an existing theme name, then page will use this theme; If the value is an nonexistent theme name, then page will use the device default theme.|
