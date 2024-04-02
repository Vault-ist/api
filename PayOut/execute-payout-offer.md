# Execute PayOut Offer

`POST` **/v4/payout/pay/{offerId}**

The endpoint is designed to execute a payout offer, meaning it allows users or applications to carry out the payout transaction specified by the given offer ID.

> 📘 This endpoint is accessible for `KYC_1` level and higher.

To use this endpoint, you need to provide the [billing address](https://github.com/Vault-ist/api/blob/main/PayIn/add-card-billing-address.md) of the card.

## Request

**Media Type:** `application/json`

### Path Parameters:
- **offerId**: string *(required)*
  - Identifier of the payout offer to be executed.

### Headers:
- **X-Sdk-Version**: string *(required)*
  - Interface build version that enables transaction operations.
  - *Example:* payoutCard=1.2

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v4/payout/pay/7493 \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTAzMjkyNjMsImlhdCI6MTcxMDI0Mjg2M30.moC63KNNib-Ohu6xEpR0WxBZiKcJ-i2oiTvyDm3YtRA' \
  --header 'Content-Type: application/json' \
  --header 'X-Sdk-Version: 1.2''
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  
Successful execution of the request indicates that the operation was successful.

- **status**: string
  - Status of the operation execution.
- **amountFrom**: integer
  - The amount that was deducted or paid out from the source currency.
- **currencyFrom**: string
  - The source currency from which the payout amount was deducted.
- **amountTo**: integer
  - The amount that was received or converted in the target currency.
- **currencyTo**: string
  - The target currency to which the payout amount was converted.

```json 
{
  "status": "SUCCESS",
  "amountFrom": 30,
  "currencyFrom": "USDT",
  "amountTo": 26.90688,
  "currencyTo": "EUR"
}
```
  
</details>


<details>
<summary><strong>400 - Bad Request</strong></summary>

The response status code indicates that the requested page was not found on the server.
  
**Media type:** `application/json`
  
  

- **message:** string
  - Message displayed to the user.

- **field:** string
  - Specifies the field in the request that caused the error.

- **errorId:** integer
  - Identifier of the error.

- **systemId:** string
  - Identifier of the component.

- **originalMessage:** string
  - The original error message.

- **errorStackTrace:** string
  - The place where the error occurred in the code.

- **data:** object
  - Additional data related to the error, structured as key-value pairs.
    - **additionalProp1:** object
    - **additionalProp2:** object
    - **additionalProp3:** object

- **error:** string
  - Identifier of the error.

    
**Responses example**

```json
{
  "error": "COMMON",
  "errorId": 0,
  "message": "Sorry for inconvenience. We're fixing the issue. If you have urgent questions, contact support",
  "systemId": "core"
}
```

</details>
