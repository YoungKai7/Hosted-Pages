
# JSON Web Tokens


The PayFabric JSON Web Tokens API is used to authentication for the Responsive Hosted Payment Page and Responsive Hosted Wallet Page. Each JWT will indicate your intent of the operation through declaration of `Audience` and `Subject`.

API Base URLs:

1. Live Server:      `https://www.payfabric.com/Payment/Web`
2. Sandbox Server:   `https://sandbox.payfabric.com/Payment/Web`

Please note that all requests require API authentication ([<kbd>🔗 LINK</kbd>](Authentication.md)).


## Generate Token for Payment Processing

* `POST /payment/api/jwt/create` will create the jwt token
* Set `Audience` to "PaymentPage.
* Set `Subject` to a [PayFabric Transaction Key](https://github.com/PayFabric/APIs/blob/master/PayFabric/Sections/Transactions.md#create-a-transaction)


<details open>
<summary> Request </summary>
<pre>
{
    <b>"Audience"</b>:"PaymentPage",
    <b>"Subject"</b>:"21040500682801"
}
</pre>
<blockquote>Required fields are marked in <b>Bold</b>. See <a href="Objects.md#json-web-tokens">object reference</a> for details.</blockquote>
</details>

<details>
<summary> Response </summary>
<pre>
{
    "Message": "",
    "Payload": {
        "aud": "PaymentPage",
        "dcn": "1",
        "device": "72972a2b-8a71-4e29-aeab-1c418b136869",
        "exp": "1617688157",
        "iat": "1617687257",
        "inst": "f242bd6d-7a23-41d7-a12e-46427ce4eba4",
        "iss": "PayFabric_V3",
        "sub": "21040500682801",
        "supportedPaymentMethods": [
            {
                "attributes": null,
                "src": "URL",
                "type": "CreditCard"
            },
            {
                "attributes": null,
                "src": "URL",
                "type": "ECheck"
            },
            {
                "attributes": [
                    {
                        "key": "data-partner-attribution-id",
                        "value": "Nodus_SP_PPCP"
                    }
                ],
                "src": "https://www.paypal.com/sdk/js?client-id=AfGQA1jQrGwqYSqbrN6M0ZnXwvDZNVKaXlNvI8VYbmb14vFWrF5CQtgw-O6xvz6n7sLtmvWJ0s0A5uW3&merchant-id=Q3E49R5X48QLG&enable-funding=venmo&disable-funding=paylater,card&currency=USD&integration-date=2021-03-16",
                "type": "PAYPAL"
            }
        ]
    },
    "Token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJQYXlGYWJyaWNfVjMiLCJpYXQiOiIxNjE3Njg3MjU3IiwiZXhwIjoiMTYxNzY4ODE1NyIsImF1ZCI6IlBheW1lbnRQYWdlIiwic3ViIjoiSFBQMjEwNDA1MDA2ODI4MDEiLCJpbnN0IjoiZjI0MmJkNmQtN2EyMy00MWQ3LWExMmUtNDY0MjdjZTRlYmE0IiwiZGV2aWNlIjoiNzI5NzJhMmItOGE3MS00ZTI5LWFlYWItMWM0MThiMTM2ODY5IiwiZGNuIjoiMSIsInN1cHBvcnRlZFBheW1lbnRNZXRob2RzIjpbeyJ0eXBlIjoiQ3JlZGl0Q2FyZCIsInNyYyI6IlVSTCIsImF0dHJpYnV0ZXMiOm51bGx9LHsidHlwZSI6IkVDaGVjayIsInNyYyI6IlVSTCIsImF0dHJpYnV0ZXMiOm51bGx9LHsidHlwZSI6IlBBWVBBTCIsInNyYyI6Imh0dHBzOi8vd3d3LnBheXBhbC5jb20vc2RrL2pzP2NsaWVudC1pZD1BZkdRQTFqUXJHd3FZU3Fick42TTBablh3dkRaTlZLYVhsTnZJOFZZYm1iMTR2RldyRjVDUXRndy1PNnh2ejZuN3NMdG12V0owczBBNXVXMyZtZXJjaGFudC1pZD1RM0U0OVI1WDQ4UUxHJmVuYWJsZS1mdW5kaW5nPXZlbm1vJmRpc2FibGUtZnVuZGluZz1wYXlsYXRlcixjYXJkJmN1cnJlbmN5PVVTRCZpbnRlZ3JhdGlvbi1kYXRlPTIwMjEtMDMtMTYiLCJhdHRyaWJ1dGVzIjpbeyJrZXkiOiJkYXRhLXBhcnRuZXItYXR0cmlidXRpb24taWQiLCJ2YWx1ZSI6Ik5vZHVzX1NQX1BQQ1AifV19XX0.grPRlquWaPWiySm6oaOLXTbQnLzM3Dz2JUtYF0pcno4"
}
</pre>
</details>



## Generate Token for a Wallet Process

### Create Wallet

* `POST /payment/api/jwt/create` will create the token
* Set `Audience` to "CreateWalletPage.
* Set `Subject` to a Customer Number

<details open>
<summary> Request </summary>
<pre>
{
    <b>"Audience"</b>:"CreateWalletPage",
    <b>"Subject"</b>:"CUST0001"
}
</pre>       
<blockquote>Required fields are marked in <b>Bold</b>. See <a href="Objects.md#json-web-tokens">object reference</a> for details.</blockquote>
</details>


<details>
<summary> Response </summary>

<pre>
{
    "Message": "",
    "Payload": {
        "aud": "CreateWalletPage",
        "dcn": "1",
        "device": "8d36dae9-312d-48fa-ad5c-fb1f6e9ad3e0",
        "exp": "1698655330",
        "iat": "1698654430",
        "inst": "530fdb82-7309-40e1-a85c-531f6f8b1a6a",
        "iss": "PayFabric_V3",
        "sub": "CUST0001",
        "supportedPaymentMethods": [],
        "supportedWalletTenderTypes": [
            "CreditCard",
            "ECheck"
        ]
    },
    "Token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJQYXlGYWJyaWNfVjMiLCJpYXQiOiIxNjk4NjU0NDMwIiwiZXhwIjoiMTY5ODY1NTMzMCIsImF1ZCI6IkNyZWF0ZVdhbGxldFBhZ2UiLCJzdWIiOiJhYmMiLCJpbnN0IjoiNTMwZmRiODItNzMwOS00MGUxLWE4NWMtNTMxZjZmOGIxYTZhIiwiZGV2aWNlIjoiOGQzNmRhZTktMzEyZC00OGZhLWFkNWMtZmIxZjZlOWFkM2UwIiwiZGNuIjoiMSIsInN1cHBvcnRlZFBheW1lbnRNZXRob2RzIjpbXSwic3VwcG9ydGVkV2FsbGV0VGVuZGVyVHlwZXMiOlsiQ3JlZGl0Q2FyZCIsIkVDaGVjayJdfQ.VrAdF2ehspqJiAq_mpyihAmYHgCjobHObc51YCk4NkM"
}	
</pre>
</details>


### Edit Wallet

* `POST /payment/api/jwt/create` will create the token
* Set `Audience` to "EditWalletPage.
* Set `Subject` to a [Wallet ID](https://github.com/PayFabric/APIs/blob/master/PayFabric/Sections/Wallets.md#create-a-credit-card)

<details open>
<summary> Request </summary>
<pre>
{
    <b>"Audience"</b>:"EditWalletPage",
    <b>"Subject"</b>:"81d824cb-4032-4532-bd18-0a2ef5ddcafc"
}
</pre>
<blockquote>Required fields are marked in <b>Bold</b>. See <a href="Objects.md#json-web-tokens">object reference</a> for details.</blockquote>
</details>

<details>
<summary> Response </summary>
<pre>
	{
    "Message": "",
    "Payload": {
        "aud": "EditWalletPage",
        "dcn": "1",
        "device": "72972a2b-8a71-4e29-aeab-1c418b136869",
        "exp": "1698655515",
        "iat": "1698654615",
        "inst": "f242bd6d-7a23-41d7-a12e-46427ce4eba4",
        "iss": "PayFabric_V3",
        "sub": "81d824cb-4032-4532-bd18-0a2ef5ddcafc",
        "supportedPaymentMethods": [],
        "supportedWalletTenderTypes": [
            "ECheck"
        ]
    },
    "Token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJQYXlGYWJyaWNfVjMiLCJpYXQiOiIxNjk4NjU0NjE1IiwiZXhwIjoiMTY5ODY1NTUxNSIsImF1ZCI6IkVkaXRXYWxsZXRQYWdlIiwic3ViIjoiODFkODI0Y2ItNDAzMi00NTMyLWJkMTgtMGEyZWY1ZGRjYWZjIiwiaW5zdCI6ImYyNDJiZDZkLTdhMjMtNDFkNy1hMTJlLTQ2NDI3Y2U0ZWJhNCIsImRldmljZSI6IjcyOTcyYTJiLThhNzEtNGUyOS1hZWFiLTFjNDE4YjEzNjg2OSIsImRjbiI6IjEiLCJzdXBwb3J0ZWRQYXltZW50TWV0aG9kcyI6W10sInN1cHBvcnRlZFdhbGxldFRlbmRlclR5cGVzIjpbIkVDaGVjayJdfQ.erOSepdA7aqKd9oUBctVpmIxj3g9GXqzQqD3lcCgErE"
}
</pre>
</details>


## Validate JSON Web Tokens


* `POST /payment/api/jwt/validate` can check if the token is valid or not.

<details open>
<summary> Request </summary>
<pre>
{
    <b>"Token"</b>:"eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJQYXlGYWJyaWNfVjMiLCJpYXQiOiIxNjE3Njg3MjU3IiwiZXhwIjoiMTYxNzY4ODE1NyIsImF1ZCI6IlBheW1lbnRQYWdlIiwic3ViIjoiSFBQMjEwNDA1MDA2ODI4MDEiLCJpbnN0IjoiZjI0MmJkNmQtN2EyMy00MWQ3LWExMmUtNDY0MjdjZTRlYmE0IiwiZGV2aWNlIjoiNzI5NzJhMmItOGE3MS00ZTI5LWFlYWItMWM0MThiMTM2ODY5IiwiZGNuIjoiMSIsInN1cHBvcnRlZFBheW1lbnRNZXRob2RzIjpbeyJ0eXBlIjoiQ3JlZGl0Q2FyZCIsInNyYyI6IlVSTCIsImF0dHJpYnV0ZXMiOm51bGx9LHsidHlwZSI6IkVDaGVjayIsInNyYyI6IlVSTCIsImF0dHJpYnV0ZXMiOm51bGx9LHsidHlwZSI6IlBBWVBBTCIsInNyYyI6Imh0dHBzOi8vd3d3LnBheXBhbC5jb20vc2RrL2pzP2NsaWVudC1pZD1BZkdRQTFqUXJHd3FZU3Fick42TTBablh3dkRaTlZLYVhsTnZJOFZZYm1iMTR2RldyRjVDUXRndy1PNnh2ejZuN3NMdG12V0owczBBNXVXMyZtZXJjaGFudC1pZD1RM0U0OVI1WDQ4UUxHJmVuYWJsZS1mdW5kaW5nPXZlbm1vJmRpc2FibGUtZnVuZGluZz1wYXlsYXRlcixjYXJkJmN1cnJlbmN5PVVTRCZpbnRlZ3JhdGlvbi1kYXRlPTIwMjEtMDMtMTYiLCJhdHRyaWJ1dGVzIjpbeyJrZXkiOiJkYXRhLXBhcnRuZXItYXR0cmlidXRpb24taWQiLCJ2YWx1ZSI6Ik5vZHVzX1NQX1BQQ1AifV19XX0.grPRlquWaPWiySm6oaOLXTbQnLzM3Dz2JUtYF0pcno4"
}
</pre>
</details>


<details>
<summary> Response - Valid JWT </summary>
<pre>
{
    "Message": null,
    "Payload": {
        "aud": "PaymentPage",
        "dcn": "1",
        "device": "72972a2b-8a71-4e29-aeab-1c418b136869",
        "exp": "1617689798",
        "iat": "1617688898",
        "inst": "f242bd6d-7a23-41d7-a12e-46427ce4eba4",
        "iss": "PayFabric_V3",
        "sub": "21040500682801",
        "supportedPaymentMethods": [
            {
                "attributes": null,
                "src": "URL",
                "type": "CreditCard"
            },
            {
                "attributes": null,
                "src": "URL",
                "type": "ECheck"
            },
            {
                "attributes": [
                    {
                        "key": "data-partner-attribution-id",
                        "value": "Nodus_SP_PPCP"
                    }
                ],
                "src": "https://www.paypal.com/sdk/js?client-id=AfGQA1jQrGwqYSqbrN6M0ZnXwvDZNVKaXlNvI8VYbmb14vFWrF5CQtgw-O6xvz6n7sLtmvWJ0s0A5uW3&merchant-id=Q3E49R5X48QLG&enable-funding=venmo&disable-funding=paylater,card&currency=USD&integration-date=2021-03-16",
                "type": "PAYPAL"
            }
        ]
    },
    "Token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJQYXlGYWJyaWNfVjMiLCJpYXQiOiIxNjE3Njg4ODk4IiwiZXhwIjoiMTYxNzY4OTc5OCIsImF1ZCI6IlBheW1lbnRQYWdlIiwic3ViIjoiSFBQMjEwNDA1MDA2ODI4MDEiLCJpbnN0IjoiZjI0MmJkNmQtN2EyMy00MWQ3LWExMmUtNDY0MjdjZTRlYmE0IiwiZGV2aWNlIjoiNzI5NzJhMmItOGE3MS00ZTI5LWFlYWItMWM0MThiMTM2ODY5IiwiZGNuIjoiMSIsInN1cHBvcnRlZFBheW1lbnRNZXRob2RzIjpbeyJ0eXBlIjoiQ3JlZGl0Q2FyZCIsInNyYyI6IlVSTCIsImF0dHJpYnV0ZXMiOm51bGx9LHsidHlwZSI6IkVDaGVjayIsInNyYyI6IlVSTCIsImF0dHJpYnV0ZXMiOm51bGx9LHsidHlwZSI6IlBBWVBBTCIsInNyYyI6Imh0dHBzOi8vd3d3LnBheXBhbC5jb20vc2RrL2pzP2NsaWVudC1pZD1BZkdRQTFqUXJHd3FZU3Fick42TTBablh3dkRaTlZLYVhsTnZJOFZZYm1iMTR2RldyRjVDUXRndy1PNnh2ejZuN3NMdG12V0owczBBNXVXMyZtZXJjaGFudC1pZD1RM0U0OVI1WDQ4UUxHJmVuYWJsZS1mdW5kaW5nPXZlbm1vJmRpc2FibGUtZnVuZGluZz1wYXlsYXRlcixjYXJkJmN1cnJlbmN5PVVTRCZpbnRlZ3JhdGlvbi1kYXRlPTIwMjEtMDMtMTYiLCJhdHRyaWJ1dGVzIjpbeyJrZXkiOiJkYXRhLXBhcnRuZXItYXR0cmlidXRpb24taWQiLCJ2YWx1ZSI6Ik5vZHVzX1NQX1BQQ1AifV19XX0.jYmTSkHVDvmQs5bNyfrDUy7Y9iSELUHo92FqsVCp5VA",
    "Valid": true
}
</pre>
</details>

<details>
<summary> Response for expired JWT </summary>
<pre>
{
    "Message": "JWT token has expired.",
    "Payload": null,
    "Token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJQYXlGYWJyaWNfVjMiLCJpYXQiOiIxNjE3Njg3MjU3IiwiZXhwIjoiMTYxNzY4ODE1NyIsImF1ZCI6IlBheW1lbnRQYWdlIiwic3ViIjoiSFBQMjEwNDA1MDA2ODI4MDEiLCJpbnN0IjoiZjI0MmJkNmQtN2EyMy00MWQ3LWExMmUtNDY0MjdjZTRlYmE0IiwiZGV2aWNlIjoiNzI5NzJhMmItOGE3MS00ZTI5LWFlYWItMWM0MThiMTM2ODY5IiwiZGNuIjoiMSIsInN1cHBvcnRlZFBheW1lbnRNZXRob2RzIjpbeyJ0eXBlIjoiQ3JlZGl0Q2FyZCIsInNyYyI6IlVSTCIsImF0dHJpYnV0ZXMiOm51bGx9LHsidHlwZSI6IkVDaGVjayIsInNyYyI6IlVSTCIsImF0dHJpYnV0ZXMiOm51bGx9LHsidHlwZSI6IlBBWVBBTCIsInNyYyI6Imh0dHBzOi8vd3d3LnBheXBhbC5jb20vc2RrL2pzP2NsaWVudC1pZD1BZkdRQTFqUXJHd3FZU3Fick42TTBablh3dkRaTlZLYVhsTnZJOFZZYm1iMTR2RldyRjVDUXRndy1PNnh2ejZuN3NMdG12V0owczBBNXVXMyZtZXJjaGFudC1pZD1RM0U0OVI1WDQ4UUxHJmVuYWJsZS1mdW5kaW5nPXZlbm1vJmRpc2FibGUtZnVuZGluZz1wYXlsYXRlcixjYXJkJmN1cnJlbmN5PVVTRCZpbnRlZ3JhdGlvbi1kYXRlPTIwMjEtMDMtMTYiLCJhdHRyaWJ1dGVzIjpbeyJrZXkiOiJkYXRhLXBhcnRuZXItYXR0cmlidXRpb24taWQiLCJ2YWx1ZSI6Ik5vZHVzX1NQX1BQQ1AifV19XX0.grPRlquWaPWiySm6oaOLXTbQnLzM3Dz2JUtYF0pcno4",
    "Valid": false
}
</pre>
</details>
