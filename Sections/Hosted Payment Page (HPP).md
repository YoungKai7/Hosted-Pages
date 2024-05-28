# Hosted Payment Page (HPP)

The PayFabric Hosted Payment Page is used for embedding the payment page through an iFrame into your application to allow your users to process a transaction.

## Table of Contents

- [Walkthrough](#walkthrough)
- [Options](#options)
- [HPP with Surcharge](#hosted-payment-page-with-surcharge)
- [HPP for Gift Card](#hosted-payment-page-for-gift-card)
- [Terminal Entry](#terminal-entry)

## Walkthrough

Before embedding the payment page, please ensure that you have done the following:

1. Generate a [Security Token](/Sections/Security%20Token.md). Assume the token value is `@TOKEN`.
2. Generate a new transaction, see our [API documentation](../../../../PayFabric-APIs/blob/master/PayFabric/Sections/Transactions.md#create-a-transaction) for how. Assume the transaction key is `@TRXKEY`.

**Note**: Hosted Payment Page will NOT load a _Verify_ transaction.

### How to Embed the HPP

Use the Transaction Key and Security Token to generate the HPP URL to use in an iFrame, replacing `{@TRXKEY}` and `{@TOKEN}` with the respective values:

https://sandbox.payfabric.com/Payment/Web/Transaction/Process?key={@TRXKEY}&token={@TOKEN}


![Hosted payment page](https://raw.githubusercontent.com/PayFabric/Portal/master/PayFabric/Sections/Screenshots/HostedPaymentPage.png "Hosted payment page")

## Options

PayFabric hosted payment page accepts the below query string parameters to add options. You can use these query parameters by adding them to your hosted payment page URL and connecting them with '&'.

| QueryString | Description |
| :------------- | ------------- |
| `Country=&Street1=&Street2=&Street3=&City=&State=&Zip=&Email=&Phone=` | This query string can pass initial billing address information. This query string only works on the hosted payment page when there is no selected wallet record. |
| `UseDefaultWallet` | When the value is `0`, the default wallet won't load while opening the hosted payment page. If set to `1`, PayFabric will load the default wallet on the hosted payment page by default. Default value is `1`. |
| `TempSave` | When the value is `1`, the user can only save the transaction on the hosted payment page. Default value is `0`. |
| `CardSwipe` | When the value is `true`, PayFabric will start processing the transaction automatically once the user swipes the card. Users can still enter card info manually by clicking the Cancel button on the pop-up card swipe message box. Default value is `false`. |
| `ThemeName` | This parameter allows a third party to dynamically pass in a theme name via query string. If the value is an existing theme name, the page will use this theme; if the value is a non-existent theme name, the page will use the device default theme. |
| `ReturnUri` | This parameter allows a third party to dynamically pass a return URL via query string. If the value is a valid URL, after the transaction is processed, the page will redirect to the return URL, and the transaction response fields will be appended to the return URL as parameters. |
| `isusenewtheme` | When the value is `1`, PayFabric's hosted page URL will trigger the V3 layout instead of V2 Layout. Default value is `0`. |
| `ProcessingMethod` | This parameter will take effect when [Payment Terminals](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Payment%20Terminals.md) are enabled. It allows third-party applications to enable/disable EMV on-the-fly on a per-transaction basis via the following query string parameter. `ProcessingMethod = 0: Web Entry only, ProcessingMethod = 1: EMV only, ProcessingMethod = 2: Both Web Entry and EMV`. |
| `UseBluefin` | This parameter will take effect when the [BlueFin Profile](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Bluefin.md) is enabled. When the value is `0`, only regular keyboard entry for credit card is available; when the value is `1`, only encryption key entry via Bluefin device for credit card is available; when the value is `2`, both regular keyboard and encryption key entry for credit card is available. |
| `useshipping` | When the value is `1`, PayFabric's checkout hosted page URL will load historical shipping addresses. When the value is `0`, PayFabric's checkout hosted page will NOT load historical shipping addresses. Default value is `1`. |
| `AuthorizationType` | The authorization type of the transaction. Valid values are `Reauthorization`, `Resubmission`, `Incremental`, or `NotSet`. |
| `TrxSchedule` | The type of authorization of the transaction to be processed. Valid values are `Unscheduled`, `ScheduledInstallment`, `ScheduledRecurring`, or `NotSet`. |
| `TrxInitiation` | The entity that initiated the transaction. Valid values are `Merchant`, `Customer`, or `NotSet`. |

## Hosted Payment Page with Surcharge

PayFabric provides the ability for merchants to support surcharges to pass on their processing costs to end customers using the EVO gateway.

1. PayFabric’s hosted payment page adds three additional fields to support surcharge: Surcharge Rate, Surcharge Amount, and Final Amount.
2. By default, these fields are hidden and will only be available if the Surcharge Rate is enabled in the gateway profile settings for the in-use gateway profile. Surcharge Amount, Surcharge Rate, and Final Amount will be read-only as they’re calculated fields by PayFabric based on the provided rate.
3. It’s up to third-party applications to design and structure these three fields using CSS/JS to fit your application’s UI and UX.

![HostedPaymentPageWithSurcharge](https://raw.githubusercontent.com/PayFabric/Portal/master/PayFabric/Sections/Screenshots/HostedPaymentPageWithSurcharge.png "Hosted Payment Page With Surcharge")

## Hosted Payment Page for Gift Card

PayFabric provides the ability for merchants to support Gift Cards on the hosted payment page. Open the transaction using the EVO Gift gateway, refer to [Gateway Account Profile](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Gateway%20Configuration.md#evo) for how to create the EVO Gift Gateway.

![GiftHPPWeb](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Screenshots/GiftHPPWEB.png)

## Terminal Entry

To enable terminal entry on the payment page, please ensure the following:

1. Create a terminal on the [Payment Terminal](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Payment%20Terminals.md) page.
2. Set the terminal for your [Device](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Payment%20Terminals.md#device-name).
3. Set the [Processing Method](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Payment%20Terminals.md#processing-method) as 'Both EMV and Web Entry' or 'EMV only'.

Then the hosted payment page will show EMV entry.

![Terminal Entry](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Screenshots/GiftHPP.png)

**Note**:
1. The Gift Card button will show on the EMV entry only when you [Allow Gift Card](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Payment%20Terminals.md#allow-gift-card).
2. When you select 'Both EMV and Web Entry', you can switch the processing method at the bottom of the hosted page.

The **Payment Terminals Signature page** is used to retrieve the PNG version of the signature for the transaction created from Payment Terminals.

Before embedding the signature page, please ensure the following:

1. Generate a [Security Token](/Sections/Security%20Token.md). Assume the token value is `@TOKEN`.
2. Generate a new transaction with Payment Terminals, see our [Payment Terminals](../../../../PayFabric/Portal/blob/master/PayFabric/Sections/Payment%20Terminals.md) for how. Assume the transaction key is `@TRXKEY`.

Open the signature page with this URL:

https://sandbox.payfabric.com/Payment/Web/Transaction/GetSignature?key={@TRXKEY}&token={@TOKEN}