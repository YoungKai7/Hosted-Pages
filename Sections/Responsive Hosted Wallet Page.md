# Responsive Hosted Wallet Page

Responsive Hosted Wallet pages enable integrators to create or update PayFabric wallets.

## Generate JWT Token

There are two responsive hosted wallet page, create and edit. Before embedding the desired wallet page, please ensure the following:

- Create Wallet Page 
  - Generate a [JWT token](../../../../PayFabric-APIs/blob/master/PayFabric/Sections/JWTToken.md) with the @CustomerName.  Assume the token value is @TOKEN.
  
  - Build the Hosted Create Wallet Page URL this way:

    https://sandbox.payfabric.com/payment/web/wallet/ResponsiveCreate?token={@TOKEN}

    ![MRHCWP](https://github.com/PayFabric/Hosted-Pages/blob/master/Sections/MRHCWP.png "MRHCWP")


- Edit Wallet Page
  - Retrieve the unique card Id, see our [API documentation](../../../../PayFabric-APIs/blob/master/PayFabric/Sections/Wallets.md#retrieve-credit-cards--echecks) for how.
  
  - Generate a [JWT token](../../../../PayFabric-APIs/blob/master/PayFabric/Sections/JWTToken.md) with the @ID.  Assume the token value is @TOKEN.
  
  - Build the Hosted Edit Wallet Page URL this way:

    https://sandbox.payfabric.com/payment/web/wallet/ResponsiveEdit?token={@TOKEN}

    ![MRHEWP](https://github.com/PayFabric/Hosted-Pages/blob/master/Sections/MRHEWP.png "MRHEWP")



## Wallet Pages

** Overview Intro

** Link to page

## Retrieve Response

