# Payment Processing
PayFabric Hosted Payment Pages offers a robust and secure solution for processing payments online. PayFabric Hosted Payment Pages can be embedded into your application to allow for processing of transactions with credit cards and/or eCheck.

PayFabric offers two different payment pages for processing payments: Responsive Hosted Payment Page (RHPP) and Hosted Payment Page (HPP). For details on the differences, see the Feature Comparison below.

## Payment Page Feature Comparison

| Feature | Responsive Hosted Payment Page (RHPP) | Hosted Payment Page (HPP) |
| ------- | ------------------------------------- | ------------------------- |
| Mobile Responsive | $${\color{green}✔}$$ | Require Custom CSS/JS |
| Supported Integration Methods | PayFabric JS SDK, iFrame | iFrame only |
| Alternative Payment Methods | Apple Pay, Google Pay, PayPal/Venmo | $${\color{red}✘}$$ |
| 3D Secure (3DS) | $${\color{green}✔}$$<sup>*</sup> | $${\color{red}✘}$$ |
| Save For Later Transaction | $${\color{red}✘}$$ | $${\color{green}✔}$$ |
| Payment Terminals | $${\color{red}✘}$$  | PAX S300, D210, and PX7 |
| Single Page UI Framework Support (React, Vue, etc.) | Seamless Integration | Requires Reloading Page |
| BlueFin Support | $${\color{green}✔}$$| $${\color{green}✔}$$ |
| Customizability | Custom CSS/JS |  Custom CSS/JS |

_<sup>*</sup>Available with EVO eService, GP API connections._

## Payment Processing Walkthrough

### Prerequisites

Before you start, ensure you have the following items ready:
   - [ ] Select the appropriate server API endpoint:
      - Live Server: `https://www.payfabric.com/Payment/Web`
      - Sandbox Server: `https://sandbox.payfabric.com/Payment/Web`

  - [ ] Review the [PayFabric Themes](https://github.com/PayFabric/Portal/blob/master/PayFabric/Sections/Themes.md) page to understand customization options.
  - [ ] Set up the appropriate branding and styling for the hosted payment page.
  - [ ] Decide whether to use the RHPP or the HPP:
      - **[Responsive Hosted Payment Page (RHPP)](../Sections/Responsive%20Hosted%20Payment%20Page%20(JavaScript%20SDK).md)**: For most use cases, use the Mobile Responsive Hosted Payment Page.
      - **[Hosted Payment Page (HPP)](../Sections/Hosted%20Payment%20Page.md)**: For use cases where payment terminals are required, or when the transaction on the payment page should be saved to be processed at a later time, utilize this hosted payment page.

### Steps for Processing a Payment: 

1. **Generate a Security Token**

   Before initiating any payment transactions, you will need to generate a security token. This token will be passed into the Authorization header when creating new transactions through the PayFabric API. See [Security Token](../Sections/Security%20Token.md) for details on generating the token.

2. **Create a Transaction**

   Once you have obtained a security token, you can proceed to create a new transaction. This involves sending a request to PayFabric with relevant transaction details, such as the amount, currency, payment gateway, and transaction type. See the [Create a Transaction](https://github.com/PayFabric/APIs/blob/master/PayFabric/Sections/Transactions.md#create-a-transaction) API for details.

   Upon a succesful request, the API will return a transaction key that will be used for generating the hosted payment page.

3. **Load Payment Page**

   Once a transaction key is generated, you may now proceed to loading the hosted page. Depending on your requirements, you can choose between two options for the payment page:
   - Option 1: **[Responsive Hosted Payment Page (RHPP)](../Sections/Responsive%20Hosted%20Payment%20Page%20(JavaScript%20SDK).md)**:  This page can be embedded through both the PayFabric JavaScript SDK as well as through an iFrame.

   - Option 2: **[Hosted Payment Page (HPP)](../Sections/Hosted%20Payment%20Page.md)**: This page is only available through iFrame.

4. **Retrieve Response**

   After a payment is processed, results can be returned in different manners, mainly directly from PayFabric service through either the back-end (most secured) or the front-end (immediate response for user experience optimization). See [Retrieve Response](../Sections/Retrieve%20Response.md) for details.





