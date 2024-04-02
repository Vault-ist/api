# Create Offer Exchange

`POST` **/v1/mobile/exchange/offer**

The endpoint is designed for users to create new exchange offers in the system, specifying details like currencies, amounts, and more, and upon successful creation, the system returns details of the created exchange offer, including its expiration period, exchange rate, and other parameters.

> ❗️ The offer is valid for **20 seconds**. After this time, the offer becomes invalid, and to create a new offer, you need to request its creation again.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Request

### Body

**Media Type:** `application/json`

- **currencyFrom**: string *(required)*
  - Currency code the user wants to exchange.
- **currencyTo**: string *(required)*
  - Currency code the user wants to exchange to.
- **amountFrom**: integer *(required)*
  - Amount of currency the user wants to exchange.
- **amountTo**: integer *(required)*
  - Amount of currency the user wants to receive in exchange.

```json 
{
  "amountTo": 0.0176517,
  "amountFrom": 30,
  "currencyTo": "EUR",
  "currencyFrom": "USDT"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v1/mobile/exchange/offer \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTA0MDI1MTgsImlhdCI6MTcxMDMxNjExOH0.1KwOo64-Aa8C0PkzGUrl4Xbovisu47tL1AqjDMpWt8E' \
  --header 'Content-Type: application/json' \
  --data '{
  "amountTo": 0.0176517,
  "amountFrom": 30,
  "currencyTo": "EUR",
  "currencyFrom": "USDT"
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>

**Media type:** `application/json`

This response provides details about the created exchange offer, including its identifier, expiration date and time, exchange rate, and details of the source and target currency amounts involved in the exchange.

- **offerId**: integer
  - Unique identifier of the created offer.
- **expirationDateTime**: string<date-time>
  - Date and time when the offer expires in ISO 8601 format.
  - *Match pattern*: YYYY-MM-DDThh:mm:ss<TZDSuffix>
- **exchangeRate**: integer
  - Exchange rate for the offer.
- **validSeconds**: integer
  - Duration of the offer's validity in seconds.
- **sourceCurrencyAmount**: object
  - Information about the amount in the source currency.
  - *amount*: integer
    - Amount of the source currency.
  - *currencyCode*: string
    - Code of the source currency.
- **targetCurrencyAmount**: object
  - Information about the amount of the target currency in the exchange offer.
  - *amount*: integer
    - Amount of currency.
  - *currencyCode*: string
    - Code of the target currency.

```json 
{
  "offerId": 7599,
  "expirationDateTime": "2024-03-13T07:50:02.220Z",
  "exchangeRate": 0.897484,
  "validSeconds": 20,
  "sourceCurrencyAmount": {
    "amount": 30,
    "currencyCode": "USDT"
  },
  "targetCurrencyAmount": {
    "amount": 26.92452,
    "currencyCode": "EUR"
  }
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
