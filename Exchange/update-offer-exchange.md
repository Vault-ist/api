# Update Existing Offer Without Charging Customer

`PUT` **/v1/mobile/exchange/offer**

The endpoint is designed to update an existing exchange offer in the system, allowing users to modify details such as currencies and amounts, and upon successful update, the system returns details of the updated exchange offer, including its expiration date and time, exchange rate, and other parameters.

> ❗️ The offer is valid for **20 seconds**. After this time, the offer becomes invalid, and to create a new offer, you need to request its creation again.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Request

**Media Type:** `application/json`

- **offerId**: integer *(required)*
  - An identifier of the offer, received in the backend response upon updating the offer.
- **currencyFrom**: string *(required)*
  - The currency the user wants to exchange.
- **currencyTo**: string *(required)*
  - The currency the user wants to receive in exchange.
- **amountFrom**: integer *(required)*
  - The amount in **CurrencyFrom** that the user wants to exchange.
- **amountTo**: integer *(required)*
  - The amount in **CurrencyTo** that the user wants to receive in exchange.

### **Example body**
```json 
{
  "offerId": 0,
  "amountTo": 0.0176517,
  "amountFrom": 30,
  "currencyTo": "EUR",
  "currencyFrom": "USDT"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request PUT \
  --url https://api.vault.sandbox.testessential.net/v1/mobile/exchange/offer \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTIxNTg1MzEsImlhdCI6MTcxMjA3MjEzMX0.KIdck2EPYJ0zyS0W7nA52ilI5t1XG4G4K9134_UTXQA' \
  --header 'Content-Type: application/json' \
  --data '{
  "offerId": 0,
  "amountTo": 0.0176517,
  "amountFrom": 30,
  "currencyTo": "EUR",
  "currencyFrom": "USDT"
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>

**Media Type:** `application/json`
  
- **offerId**: integer
  - The identifier of the updated offer.
- **expirationDateTime**: string<date-time>
  - Specifies the date and time when the updated offer will expire. Matches the pattern: YYYY-MM-DDThh:mm:ss<TZDSuffix>.
- **exchangeRate**: integer
  - The exchange rate for the updated offer.
- **validSeconds**: integer
  - Indicates the duration for which the offer remains valid.
- **sourceCurrencyAmount**: object
  - Contains details about the amount of the source currency involved in the exchange.
  - *amount*: integer
    - The amount of the source currency involved in the exchange.
  - *currencyCode*: string
    - The currency code of the source currency.
- **targetCurrencyAmount**: object
  - Contains details about the amount and currency code of the target currency.
  - *amount*: integer
    - The amount of the target currency to be received in exchange.
  - *currencyCode*: string
    - The currency code of the target currency.


```json 
{
  "offerId": 9100,
  "expirationDateTime": "2024-04-02T17:17:52.855Z",
  "exchangeRate": 0.9114,
  "validSeconds": 20,
  "sourceCurrencyAmount": {
    "amount": 30,
    "currencyCode": "USDT"
  },
  "targetCurrencyAmount": {
    "amount": 27.342,
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
