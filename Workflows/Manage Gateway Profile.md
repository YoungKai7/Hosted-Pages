# Manage Gateway Profile

You can embed PayFabric’s Gateway Profile Page within an iFrame to allow internal admin users to manage gateway profiles directly from your application.

## Prerequisites

Before embedding the gateway profile page, ensure the following:

1. **Generate a Security Token**: Follow the instructions [here](/Sections/Security%20Token.md) to generate a security token. Assume the token value is `@TOKEN`.
2. **Retrieve the Unique Gateway ID** (if updating existing gateway): Refer to our [API documentation](https://github.com/PayFabric/APIs/blob/master/PayFabric/Sections/Payment%20Gateway%20Profiles.md#retrieve-a-payment-gateway-profile) to learn how to retrieve the unique gateway ID. Assume the gateway ID is `@GATEWAYID`.

## Create a Gateway Profile

To create a new gateway profile, construct the hosted create gateway profile page URL as follows:

https://sandbox.payfabric.com/payment/web/transaction/hostnewgateway?token=@TOKEN


![Hosted create gateway profile page](https://raw.githubusercontent.com/PayFabric/Portal/master/PayFabric/Sections/Screenshots/HostedCreateGatewayPage.png)

## Update a Gateway Profile

To update an existing gateway profile, construct the hosted update gateway profile page URL as follows:

https://sandbox.payfabric.com/payment/web/transaction/hosteditgateway?id={@GATEWAYID}&token={@TOKEN}


![Hosted update gateway profile page](https://raw.githubusercontent.com/PayFabric/Portal/master/PayFabric/Sections/Screenshots/HostedUpdateGatewayPage.png) 

## Options

The PayFabric hosted gateway profile page accepts the following query string parameters to add options. You can include these parameters by adding them to your hosted gateway profile page URL and connecting them with `&`.

| Query String | Description |
|:-------------|:-------------|
| `ThemeName=` | Pass a theme name dynamically via the query string. If the value is an existing theme name, the page will use that theme; if not, it will use the default theme. See [Themes](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Themes.md) for details on using and customizing themes. |
| `ReturnURI=` | Pass a return URL dynamically via the query string. If the value is a valid URL, after the gateway profile is saved, the page will redirect to the return URL with the unique gateway ID appended. (Note: This parameter is only for the hosted create gateway profile page.) |
