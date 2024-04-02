# Create Payout Offer

`POST` **/v4/payout/offer**

The endpoint is designed to create a payout offer. It allows users or applications to specify details for a payout transaction and receive information about the offer that can be accepted.

> ❗️ The offer is valid for **20 seconds**. After this time, the offer becomes invalid, and to create a new offer, you need to request its creation again.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Request

### Body

**Media Type:** `application/json`

Headers

- **X-Sdk-Version**: string *(required)*
  - Interface build version that enables transaction operations.
  - *Example:* payoutCard=1.2

Body

- **amount**: integer *(required)*
  - The amount of funds to be transferred in the specified currency.

- **fromCurrency**: string *(required)*
  - The currency from which the funds will be transferred.

- **toCurrency**: string *(required)*
  - The currency to which the funds will be converted.

- **cardId**: integer *(required)*
  - The ID of the card from which the funds will be transferred.


```json 
{
  "amount": 760.06209697,
  "cardId": 432154325048,
  "toCurrency": "EUR",
  "fromCurrency": "USDT"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v4/payout/offer \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: application/json' \
  --header 'X-Sdk-Version: payoutCard=1.2' \
  --data '{
  "amount": 760.06209697,
  "cardId": 432154325048,
  "toCurrency": "EUR",
  "fromCurrency": "USDT"
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>

**Media type:** `application/json`
  
200 OK status.

  - *offerId*: integer
    - The unique identifier for the payout offer.
  - *validSeconds*: integer
    - The duration for which the offer remains valid.
  - *amount*: integer
    - The amount specified in the offer.
  - *currencyFrom*: string
    - The currency from which the funds will be transferred.
  - *amountTo*: integer
    - The amount to be received in the target currency.
  - *currencyTo*: string
    - The currency to which the funds will be converted.
  - *rate*: integer
    - The exchange rate used for currency conversion.
  - *feeInfo*: array[object]
    - Information about any applicable fees, including the currency, name, scale, value, and type of fee.
      - *currency*: string
        - The currency of the fee.
      - *name*: string
        - The name of the fee.
      - *scale*: integer
        - The scale of the fee.
      - *value*: integer
        - The value of the fee.
      - *type*: string
        - The type of fee.
  - *possibleToExecute*: boolean
    - A boolean indicating whether it is possible to execute the payout offer.
  - *limit*: object
    - Details about any applicable limits on the transfer, including the value and currency.
      - *value*: integer
        - The value of the limit.
      - *currency*: string
        - The currency of the limit.
          
```json 
{
  "offerId": 9096,
  "validSeconds": 20,
  "amount": 760.06209697,
  "currencyFrom": "USDT",
  "amountTo": 692.4971369219488,
  "currencyTo": "EUR",
  "rate": 0.911106,
  "feeInfo": [
    {
      "currency": "USDT",
      "name": "Transaction fee",
      "scale": 8,
      "value": 29.29092365395,
      "type": "TRANSACTION_FEE"
    },
    {
      "currency": "USDT",
      "name": "Crypterium GAS",
      "scale": 8,
      "value": 0,
      "type": "CRYPTERIUM_GAS"
    },
    {
      "currency": "USDT",
      "name": "Additional fee",
      "scale": 8,
      "value": 0,
      "type": "ADDITIONAL_FEE"
    }
  ],
  "possibleToExecute": false,
  "limit": {
    "value": 0,
    "currency": "EUR"
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
