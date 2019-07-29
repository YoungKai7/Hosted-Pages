Retrieve Response
===================

Below methods serves the purpose of retrieving the response from embeded the hosted page in a Windows orm.

`OnTransactionCompleted(TrxKey, RespStatus, ResultCode, AuthCode, ResponseMsg, OriginationID, RespTrxTag, CVV2Response, AVSAddressResponse, AVSZipResponse, IAVSAddressResponse)` will be invoked when the transaction has been processed on hosted payment page. 

`OnSaveTransactionCompleted(TrxKey, BatchNumber, Result, ResponseMsg)` will be invoked when the transaction has been saved on hosted payment page.

`OnWalletCreateCompleted(CardID, IsCancel)` will be invoked when the wallet has been created successfully on hosted wallet page.

`OnWalletUpdateCompleted(CardID, Result, IsCancel)` will be invoked when the wallet has been updated successfully on hosted wallet page.

Example
--------------------

1. Load the hosted page in a Web Browser Control form and register TrxNotifyScript() on the form.
namespace MyProject
{
    private void PF_HostedPage_Form_Load(object sender, EventArgs e)
    {
        checkOutPage_web.ObjectForScripting = new TrxNotifyScript();
    }
}

2. Class TrxNotifyScript provides methods to return the results from the hosted page:
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



