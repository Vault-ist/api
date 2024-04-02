# Execute Offer Payment (do payment authorization)

`POST` **/v3/payin/pay/{offerId}**

The endpoint is intended for carrying out the actual payment within the context of the offer and for performing payment authorization.

> 📘 This endpoint is accessible for `KYC_1` level and higher.

## Request

**Media Type:** `application/json`

### Path Parameters
- **offerId**: string *(required)*
  - Unique identifier of the offer for which the payment needs to be executed.

### Body
- **cardCVV**: string
  - The CVV code of the card for payment authorization.
- **successUrl**: string
  - The URL to redirect to upon successful payment.
- **fingerprint**: object
  - Contains various parameters related to browser fingerprinting for security and fraud prevention.
  - **timezone**: integer
    - The timezone of the browser.
  - **browserColorDepth**: integer
    - The color depth of the browser.
  - **browserLanguage**: string
    - The language of the browser.
  - **browserScreenHeight**: integer
    - The height of the browser screen.
  - **browserScreenWidth**: integer
    - The width of the browser screen.
  - **browserPixelDepth**: integer
    - The pixel depth of the browser.
  - **browserPixelRatio**: string
    - The pixel ratio of the browser.
  - **browserViewportHeight**: integer
    - The viewport height of the browser.
  - **browserViewportWidth**: integer
    - The viewport width of the browser.
  - **browserAcceptHeader**: string
    - The accept header of the browser.
  - **os**: string
    - The operating system of the browser.
  - **browserJavascriptEnabled**: boolean
    - Indicates if JavaScript is enabled in the browser.
    - *Default*: true
  - **browserJavaEnabled**: boolean
    - Indicates if Java is enabled in the browser.
    - *Default*: true

```json 
{
  "cardCVV": "***",
  "fingerprint": {
    "acceptContent": "text/html,application/xhtml+x0.8",
    "browserLanguage": "en-us",
    "browserColorDepth": 32,
    "browserJavaEnabled": false,
    "browserScreenWidth": 428,
    "browserAcceptHeader": "text/html,applicat+xm=0.8",
    "browserScreenHeight": 884,
    "browserJavascriptEnabled": true
  }
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v3/payin/pay/12345 \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: application/json' \
  --data '{
  "cardCVV": "***",
  "fingerprint": {
    "acceptContent": "text/html,application/xhtml+x0.8",
    "browserLanguage": "en-us",
    "browserColorDepth": 32,
    "browserJavaEnabled": false,
    "browserScreenWidth": 428,
    "browserAcceptHeader": "text/html,applicat+xm=0.8",
    "browserScreenHeight": 884,
    "browserJavascriptEnabled": true
  }
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  

- **successUrl**: string
  - URL for successful redirection after payment execution.
- **failUrl**: string
  - URL for redirection in case of unsuccessful payment.
- **cancelUrl**: string
  - URL for redirection in case of payment cancellation.
- **authLink**: string
  - Link to the payment authorization page.
- **offerId**: integer
  - Unique identifier of the offer.
- **transactionStatus**: string
  - The status of the transaction.
- **transactionStatusCode**: integer
  - The status code of the transaction.
- **originalTransactionStatus**: string
  - The original status of the transaction.
- **originalTransactionStatusCode**: integer
  - The original status code of the transaction.
- **paymentMode**: string
  - The payment mode used for the transaction.
- **maskedPan**: string
  - The masked PAN (Primary Account Number) of the card used for payment.
- **transactionDate**: string
  - The date of the transaction.
- **transactionAmount**: string
  - The amount of the transaction.
- **cardCountryCode**: string
  - The country code of the card issuer.
- **cardCountryName**: string
  - The name of the card issuer's country.
- **cardBankName**: string
  - The name of the card issuer's bank.

```json 
{
  "failUrl": null,
  "offerId": 7404,
  "authLink": null,
  "cancelUrl": null,
  "maskedPan": "490742****3896",
  "successUrl": null,
  "paymentMode": "debit",
  "cardBankName": "WINSTON-SALEM FEDERAL CREDIT UNION",
  "cardCountryCode": "US",
  "cardCountryName": "USA",
  "transactionDate": "2024-03-12T11:23:20",
  "transactionAmount": "32.09",
  "transactionStatus": "Wrong response from provider",
  "transactionStatusCode": 305,
  "originalTransactionStatus": "Wrong response from provider",
  "originalTransactionStatusCode": 305
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
