## Hosted Gateway Profile Page

Ability to embed PayFabric’s gateway profile page in an iFrame to allow internal admin user to manage gateway account profile from application.

Before embedding the wallet page, please ensure the following:

1. Generate a [Security Token](../../../../PayFabric-APIs/blob/master/Sections/Authentication.md#security-token).  Assume the token value is @TOKEN.
2. If updating, retrieve the unique gateway Id, see our [API documentation](blob/master/Sections/Payment%20Gateway%20Profiles.md#retrieve-payment-gateway-profiles) for how.  Assume the card Id is @GATEWAYID.

Create a Gateway
-----------------------------

Build the hosted create gateway profile page URL this way:

https://sandbox.payfabric.com/Payment/Web/Transaciton/HostNewGateway?token=@TOKEN  

![Hosted create gateway profile page](https://s3-us-west-1.amazonaws.com/github-screenshot-repository/V3/HostedCreateGatewayPage.png)

Update a Credit Card / eCheck
-----------------------------

Build the hosted update gateway profile page URL this way:

https://sandbox.payfabric.com/Payment/Web/Transaction/HostEditGateway?id={@GATEWAYID}&token={@TOKEN}

![Hosted update gateway profile page](https://s3-us-west-1.amazonaws.com/github-screenshot-repository/V3/HostedUpdateGatewayPage.png) 

Options
-------

PayFabric hosted gateway profile page accepts the below query string parameters to add options. You can use below query parameters by adding them to your hosted gateway profile page URL and connecting them with '&'.

>
| QueryString| Description | 
|:------------- | :------------- | 
|ThemeName=|This parameter is to support 3rd party dynamically pass into theme name via query string. If the value is an existing theme name, then page will use this theme; If the value is an nonexistent theme name, then page will use the device default theme.|
|ReturnURI=|This parameter is to support 3rd party dynamically pass a return url via query string. If the value is a valid URL, then after the wallet is saved, page will redirect to the return url, and the unique gateway ID will be appended to the return URL. (note: the parameter is only for hosted create gateway profile page.)|
