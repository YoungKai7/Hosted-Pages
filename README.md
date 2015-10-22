PayFabric Hosted Pages
======================
PayFabric hosted pages are secure pages that can be embedded into your application, to allow for processing of the transactions or creating new credit card or eCheck entries into a customer’s wallet. Below are the base URLs:

1. Live Server:    ``https://www.payfabric.com/V2/Web``
1. Sandbox Server: ``https://sandbox.payfabric.com/V2/Web``

Where do I start?
-----------------

Want to get started with PayFabric Hosted Page integration? Here's a quick check list:

1. Register and then configure a PayFabric account, check out the [Quick Start Guide](https://github.com/PayFabric/Portal/wiki) to learn how.
2. Read up on how to generate a [Security Token](https://github.com/ShaunSharples/APIs/blob/ShaunSharples-patch-1/Sections/Authentication.md#security-token) as our hosted pages require this. 
3. Choose the hosted page you need to work with.
4. Have a question or need help? Contact <support@payfabric.com>.

Payment Page
------------

The payment page is used for embedding a page to process an existing transaction.

We have a [detailed guide](https://github.com/ShaunSharples/HostedPages/blob/master/Sections/PaymentPage.md) for getting started with embedding the payment page into your application.

Wallet Page
-----------

The wallet page is used for embedding a page to create or modify credit card or eCheck entries.

We have a [detailed guide](https://github.com/ShaunSharples/HostedPages/blob/master/Sections/WalletPage.md) for getting started with embedding the wallet page into your application.

Customize Page
--------------

Both the payment and wallet pages are able to be customized with a custom theme consisting of custom CSS and JavaScript, which will be inserted into and applied to the hosted pages.  We have a [detailed guide](https://github.com/PayFabric/Portal/wiki/Themes) for creating and using these customized themes.
