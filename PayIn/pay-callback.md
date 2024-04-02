# Pay Callback

`GET` **/v3/payin/pay-callback**

The endpoint serves to provide information about the outcome of a payment operation, notifying or callback to the client system following the completion of a payment transaction initiated through an offer.

> 📘 This endpoint is accessible for `KYC_1` level and higher.

## Request

**Media Type:** `application/json`

### Query Parameters

- **offerId**: `integer<int64>` *(required)*  
  - Unique identifier of the offer for which the payment callback information is requested.
  

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request GET \
  --url 'https://api.vault.sandbox.testessential.net/v3/payin/pay-callback?offerId+=234355' \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>

**Media Type:** `application/json`
  

- **offerId**: integer
  - Unique identifier of the associated offer.
- **status**: string
  - Payment status, indicating whether the transaction was successful.
- **amount**: integer
  - The total amount involved in the transaction.
- **currency**: string
  - The currency of the transaction amount.
- **cryptoAmount**: integer
  - The amount in cryptocurrency.
- **cryptoCurrency**: string
  - The cryptocurrency used in the transaction.
- **maskedPan**: string
  - Masked card number for privacy.
- **transactionStatus**: string
  - Current status of the transaction.
- **transactionStatusCode**: integer
  - Numeric code indicating the status of the transaction.
- **originalTransactionStatus**: string
  - Original transaction status.
- **originalTransactionStatusCode**: integer
  - Original transaction status code.
- **paymentMode**: string
  - Mode of payment used for the transaction.
- **transactionDate**: string
  - Date of the transaction. In ISO 8601 format.
  - *Example*: `2024-01-23T15:05:03.022Z`
- **transactionAmount**: string
  - Transaction amount in string format.
- **cardCountryCode**: string
  - Country code associated with the card used in the transaction.
- **cardCountryName**: string
  - Country name associated with the card used in the transaction.
- **cardBankName**: string
  - Bank name associated with the card used in the transaction.
- **blockedAmount**: object
  - Information about any blocked amount.
    - **value**: integer
      - The value of the blocked amount.
    - **currency**: string
      - The currency of the blocked amount.

```json 
{
  "amount": 470,
  "status": "FAILURE",
  "offerId": 5423432476,
  "currency": "EUR",
  "maskedPan": "142141****23414",
  "paymentMode": "debit",
  "cardBankName": "PAYSAFE FINANCIAL SERVICES, LTD.",
  "cryptoAmount": 0.01833081,
  "blockedAmount": {
    "value": 0,
    "currency": "EUR"
  },
  "cryptoCurrency": "BTC",
  "cardCountryCode": "GR",
  "cardCountryName": "PAYSAFE FINANCIAL SERVICES, LTD.",
  "transactionDate": "2023-09-16T11:08:05",
  "transactionAmount": "474.7",
  "transactionStatus": "Do not honour",
  "transactionStatusCode": 400,
  "originalTransactionStatus": "Do not honour",
  "originalTransactionStatusCode": 400
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
