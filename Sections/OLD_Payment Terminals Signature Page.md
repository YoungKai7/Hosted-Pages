Payment Terminals Signature Page
===================

The Payment Terminals Signature page is used to retrieve the PNG version of the signature for the transaction created from Payment Terminals.

Before embedding the signature page, please ensure the following:

1. Generate a [Security Token](/Sections/Security%20Token.md).  Assume the token value is @TOKEN.
2. Generate a new transaction with Payment Terminals, see our [Payment Terminals](../../../../PayFabric/Portal/blob/master/PayFabric/Sections/Payment%20Terminals.md) for how.  Assume the transaction key is @TRXKEY.

Open the signature page with this URL:

https://sandbox.payfabric.com/Payment/Web/Transaction/GetSignature?key={@TRXKEY}&token={@TOKEN}

Test