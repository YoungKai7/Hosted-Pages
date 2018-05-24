Hosted Wallet Page
==================

The PayFabric hosted wallet page is used for embedding the wallet page into your application to allow your users to create or update their credit card / eCheck details (including billing address information).

Before embedding the wallet page, please ensure the following:

1. Generate a [Security Token](/Sections/Security%20Token.md).  Assume the token value is @TOKEN.
2. If updating, retrieve the unique card Id, see our [API documentation](../../../../PayFabric-APIs/blob/master/PayFabric/Sections/Wallets.md#retrieve-credit-cards--echecks) for how.  Assume the card Id is @CARDID.
 
Create a Credit Card / eCheck
-----------------------------

Build the hosted create wallet page URL this way:

https://sandbox.payfabric.com/Payment/Web/Wallet/Create?customer={CUSTOMER_NUMBER}&tender={TENDER}&token={@TOKEN}  

{CUSTOMER_NUMBER} = Your customers unique identifier  
{TENDER} = *CreditCard* or *ECheck*

![Hosted create wallet page](https://s3-us-west-1.amazonaws.com/github-screenshot-repository/v2/HostedCreateWalletPage.png "Hosted create wallet page")


Update a Credit Card / eCheck
-----------------------------

Build the hosted update wallet page URL this way:

https://sandbox.payfabric.com/Payment/Web/Wallet/edit?card={@CARDID}&token={@TOKEN}

![Hosted update wallet page](https://s3-us-west-1.amazonaws.com/github-screenshot-repository/v2/HostedEditWalletPage.png "Hosted update wallet page") 

Options
-------

PayFabric hosted wallet page accepts the below query string parameters to add options. You can use below query parameters by adding them to your hosted wallet page URL and connecting them with '&'.

>
| QueryString| Description | 
| :------------- | :------------- | 
|Country=&Street1=&Street2=&Street3=<br/>&City=&State=&Zip=&Email=&Phone= |This query string can pass initial billing address information|
|ThemeName|This parameter is to support 3rd party dynamically pass into theme name via query string. If the value is an existing theme name, then page will use this theme; If the value is an nonexistent theme name, then page will use the device default theme.|
|ReturnURI|This parameter is to support 3rd party dynamically pass a return url via query string. If the value is a valid URL, then after the wallet is saved, page will redirect to the return url, and the unique Wallet ID will be appended to the return URL. (note: the parameter is only for hosted create wallet page.)|
|isusenewtheme|	When the value is `1`, PayFabric's hosted page URL will trigger the V3 layout instead of V2 Layout. Default value is `0`|
|UseBluefin|This parameter will take affect when [BlueFin Profile](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Bluefin.md) get enabled. When the value is '0', only regular keybaord entry for credit card is available, when the value is `1`, only encryption key entry via Bluefin device for credit card is available, when the value is `2`, both regular keyboard & encryption key entry for credit card is available.|
