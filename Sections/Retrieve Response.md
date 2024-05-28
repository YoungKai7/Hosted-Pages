# Retrieve Response

After a payment is processed, results can be returned in different manners, mainly directly from PayFabric service through back-end (most secure) or front-end (immediate response for user experience optimization).

## Table of Contents

- [Back-End Response Retrieval](#back-end-response-retrieval)
  - [Option 1: Post URL (Push)](#option-1-post-url-push)
  - [Option 2: API Query (Pull)](#option-2-api-query-pull)
- [Front-End Response Retrieval](#front-end-response-retrieval)
  - [Option 1: Window Event Message](#option-1-window-event-message)
- [Windows Forms Application](#windows-forms-application)
  - [Example](#example)

## Back-End Response Retrieval

### Option 1: Post URL (Push)

Configure the Post URL for the Device under PayFabric Settings on the PayFabric portal. The response will be posted to the Post URL after the transaction is processed.

**Example HTTP POST request body:**
```
InstID=2c1c8310-703a-4e2e-b115-c08a0bb5cb5e&DeviceID=aff49c4f-472e-cfe1-788b-e92697b9ac37&TrxKey=22012001587025&TenderType=CreditCard&TrxType=Sale&TrxAmount=10.00&SurchargeAmount=0&SurchargePercentage=0&FinalAmount=10.00&CardType=Credit&AccountNumber=XXXXXXXXXXXX1111&ABANumber=&MICRNumber=&CheckNumber=&Status=Approved&RespStatus=Approved&OriginationID=CC38847CA5574DAD85A71AB77FF900E4&TrxTag=1/21/2022 2:25:02 AM&RespTrxTag=1/21/2022 2:25:02 AM&AuthCode=I3MZFF&ResultCode=1&ResponseMsg=APPROVED&CVV2Response=NotSet&AVSAddressResponse=&AVSZipResponse=&IAVSAddressResponse=&TrxDate=1/20/2022 8:25:02 PM&GatewayTransactionID=CC38847CA5574DAD85A71AB77FF900E4&ExpectedSettledTime=2022-01-22T04:00:00.0000000Z&SettledTime=&WalletID=8379d297-eb79-452e-9e3e-d10f9f6d667c
```


Response From Your Endpoint (Post URL) is Recorded:
We log and store the response coming back from your endpoint when performing a post-back to your Post URL. Please make sure that your response does not contain any sensitive data.

### Option 2: API Query (Pull)

Use the following APIs to query for the record details:
- [Retrieve a Transaction](https://github.com/PayFabric/APIs/blob/master/PayFabric/Sections/Transactions.md#retrieve-a-transaction)
- [Retrieve a Credit Card / eCheck](https://github.com/PayFabric/APIs/blob/master/PayFabric/Sections/Wallets.md#retrieve-a-credit-card--echeck)

## Front-End Response Retrieval

Front-end code is susceptible to user tinkering. While this method provides immediate feedback to optimize user experience, it is best security practice to couple it with a back-end method to obtain reliable response results.

### Option 1: Window Event Message

After a Hosted Page completes processing, a window event is triggered with a response message composed in JSON string format, with "Event" set to one of the following.

#### Events Available with Hosted Payment Page (HPP)
- OnTransactionCompleted
- OnSaveTransactionCompleted

#### Events Available with Responsive Hosted Payment Page (RHPP)
- readyCallback
- transaction3DSChallengeCallback
- successCallback
- cancelCallback
- failureCallback
- transactionProcessingCallback
- transactionStoppedProcessingCallback

#### Events Available with Hosted Wallet Page
- OnWalletCreateCompleted
- OnWalletUpdateCompleted

#### Events Available with Responsive Hosted Wallet Pages
- successCallback
- failureCallback
- cancelCallback
- readyCallback
- transactionProcessingCallback
- transactionStoppedProcessingCallback

Add an Event Listener on your page to get the response message.

**Example JavaScript code:**
```javascript
window.addEventListener('message', function(event) {
  var objMsg;
  objMsg = JSON.parse(event.data);

  // For best security practice, only accept event message from specified domain.
  if (event.origin !== 'https://sandbox.payfabric.com') return;
  switch (objMsg.Event) {
    case "OnSaveTransactionCompleted":
      // your code
      break;
    case "OnTransactionCompleted":
      // your code
      break;
    case "OnWalletCreateCompleted":
      // your code
      break;
    case "OnWalletUpdateCompleted":
      // your code
      break;
  }
}, false);
```

<details>
  <summary>Example response string (HPP):</summary>

  ```json
  {
    "Event": "OnTransactionCompleted",
    "TrxKey": "19111500384554",
    "RespStatus": "Approved",
    "ResultCode": "1",
    "AuthCode": "1AR1IJ",
    "ResponseMsg": "APPROVED",
    "OriginationID": "6552A51518F54AC38B84164EE69965BA",
    "RespTrxTag": "11/21/2019 9:55:01 PM",
    "CVV2Response": "NotProcessed",
    "AVSAddressResponse": "Match",
    "AVSZipResponse": "Match",
    "IAVSAddressResponse": ""
  }
```
</details>

<details>
<summary>Example response string (RHPP):</summary>

```json
{
  "Event": "successCallback",
  "TrxKey": "24030705381773",
  "RespStatus": "Approved",
  "ResultCode": "1",
  "AuthCode": "QQS1H8",
  "ResponseMsg": "APPROVED",
  "OriginationID": "D01DCB9C04C74F82888F54E89BEE6B0D",
  "CVV2Response": "NotSet",
  "AVSAddressResponse": null,
  "AVSZipResponse": null,
  "IAVSAddressResponse": null,
  "ResultStatus": "True",
  "PayFabricErrorCode": null,
  "RespTrxTag": "3/7/2024 5:13:21 PM",
  "TerminalID": null,
  "TerminalResultCode": null,
  "OrigTrxAmount": "10.00",
  "SurchargeAmount": "0.00",
  "SurchargePercentage": "0.00",
  "TrxAmount": "10.00",
  "FinalAmount": "10.00",
  "CardType": "Debit",
  "ExpectedSettledTime": "3/7/2024 8:00:00 PM",
  "ExpectedSettledTimeUTC": "2024-03-08T04:00:00.000",
  "SettledTime": null,
  "SettledTimeUTC": null,
  "WalletID": "e57b52fd-2cea-4824-b82d-d5c3705e9328",
  "TrxDate": "3/7/2024 11:13:25 AM",
  "TrxDateUTC": "2024-03-07T19:13:25.122",
  "FraudScore": null,
  "IncriminatingText": null,
  "ExoneratingText": null,
  "RemainingBalance": null
}
```

</details>


## Windows Form Application

Below methods serve the purpose of retrieving the response from embedded hosted page in a Windows Forms application.

`OnTransactionCompleted(TrxKey, RespStatus, ResultCode, AuthCode, ResponseMsg, OriginationID, RespTrxTag, CVV2Response, AVSAddressResponse, AVSZipResponse, IAVSAddressResponse)` will be invoked when the transaction has been processed on hosted payment page. 

`OnSaveTransactionCompleted(TrxKey, BatchNumber, Result, ResponseMsg)` will be invoked when the transaction has been saved on hosted payment page.

`OnWalletCreateCompleted(CardID, IsCancel)` will be invoked when the wallet has been created successfully on hosted wallet page.

`OnWalletUpdateCompleted(CardID, Result, IsCancel)` will be invoked when the wallet has been updated successfully on hosted wallet page.

### Example

1. Load the hosted page in a Web Browser Control form and register TrxNotifyScript() on the Windows Form.
```C#
namespace MyProject
{
    private void PF_HostedPage_Form_Load(object sender, EventArgs e)
    {
        checkOutPage_web.ObjectForScripting = new TrxNotifyScript();
    }
}
```
2. Class TrxNotifyScript provides methods to return the results from the hosted page.
```C#
namespace MyProject
{
    [System.Runtime.InteropServices.ComVisibleAttribute(true)]
    public class TrxNotifyScript
    {
        public void OnTransactionCompleted(
            string TrxKey,
            string RespStatus,
            string ResultCode,
            string AuthCode,
            string ResponseMsg,
            string OriginationID,
            string RespTrxTag,
            string CVV2Response,
            string AVSAddressResponse,
            string AVSZipResponse,
            string IAVSAddressResponse)
        {
            // Your code
        }
        
        public void OnSaveTransactionCompleted(
            string TrxKey,
            string BatchNumber,
            bool Result,
            string ResponseMsg)
        {
            // Your code
        }
        
        public void OnWalletCreateCompleted(
            string CardID,
            string IsCancel)
        {
            // Your code
        }
        
        public void OnWalletUpdateCompleted(
            string CardID,
            bool Result,
            string IsCancel)
        {
            // Your code
        }
    }
}
```


