# Create Offer Without Charging Customer

`POST` **/v3/payin/offer**

This endpoint facilitates the creation of an offer without actually charging the customer. It is useful when generating preliminary details of a transaction or payment operation.

> ❗️ The offer is valid for **20 seconds**. After this time, the offer becomes invalid, and to create a new offer, you need to request its creation again.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Request

### Body

**Media Type:** `application/json`

- **cardId**: integer *(required)*
  - The unique identifier of the card associated with the operation.
- **fromCurrency**: string *(required)*
  - The currency from which the operation is conducted.
- **amount**: integer *(required)*
  - The amount of the operation proposed to the customer.
- **toCurrency**: string *(required)*
  - The currency to which the operation is applied.
- **operation**: string
  - The type of operation, in this case, "PAYIN" (deposit).

```json 
{
  "amount": 31,
  "cardId": 1,
  "operation": "PAYIN",
  "toCurrency": "USDC",
  "fromCurrency": "EUR"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v3/payin/offer \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: application/json' \
  --data '{
  "amount": 31,
  "cardId": 1,
  "operation": "PAYIN",
  "toCurrency": "USDC",
  "fromCurrency": "EUR"
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>

**Media type:** `application/json`
  
200 OK status and provides detailed information about the created offer.

- **offerId**: integer
  - The unique identifier of the created offer.
- **expirationTime**: string
  - The time when the offer expires.
- **validSeconds**: integer
  - The number of seconds during which the offer is valid.
- **fromCurrency**: string
  - The currency of the operation.
- **rate**: object
  - Information about the exchange rate.
  - **rate**: integer
    - The exchange rate.
  - **currency**: string
    - The currency for the exchange.
  - **commissionFix**: integer
    - Fixed commission.
  - **commissionPercentage**: integer
    - Percentage commission.
  - **minCrypto**: integer
    - Minimum amount in cryptocurrency.
  - **maxCrypto**: integer
    - Maximum amount in cryptocurrency.
- **feeInfo**: array[object]
  - An array with information about fees.
  - **name**: string
    - The name of the fee.
  - **value**: integer
    - The value of the fee.
  - **valueOld**: integer
    - The old value of the fee.
  - **scale**: integer
    - The scale of the fee.
  - **currency**: string
    - The currency of the fee.
- **limit**: object
  - An object indicating the limit of the offer.
  - **value**: integer
    - The value of the limit.
  - **currency**: string
    - The currency of the limit.
- **fees**: object
  - An object containing various fees.
  - **currency**: string
    - The currency of the fees.
  - **scale**: integer
    - The scale of the fees.
  - **rate**: integer
    - The rate of the fees.
  - **partnerFee**: integer
    - Partner fee.
  - **crypteriumGas**: integer
    - Crypterium gas fee.
  - **additionalFee**: integer
    - Additional fee.
  - **transactionFee**: integer
    - Transaction fee.
  - **insuranceFee**: integer
    - Insurance fee.
  - **feeTableEnabled**: boolean
    - Whether the fee table is enabled.
  - **feeTable**: array[object]
    - An array with information about the fee table.

```json 
{
  "fees": {
    "rate": 0.03,
    "scale": 8,
    "currency": "EUR",
    "feeTable": [
      {
        "percent": 1.5,
        "amountTo": {
          "value": 250,
          "currency": "EUR"
        },
        "amountFrom": {
          "value": 0,
          "currency": "EUR"
        }
      },
      {
        "percent": 0.5,
        "amountTo": null,
        "amountFrom": {
          "value": 250,
          "currency": "EUR"
        }
      }
    ],
    "partnerFee": 0,
    "insuranceFee": null,
    "crypteriumGas": 0,
    "transactionFee": 0
  },
  "rate": {
    "rate": 0.00003919001906978183,
    "currency": "EUR",
    "maxCrypto": 0,
    "minCrypto": 0,
    "commissionFix": 0,
    "commissionPercentage": 0
  },
  "feeInfo": [
    {
      "name": "Crypterium gas",
      "scale": 8,
      "value": 0,
      "currency": "EUR",
      "valueOld": 0
    },
    {
      "name": "Transaction fee",
      "scale": 8,
      "value": 0,
      "currency": "EUR",
      "valueOld": 0.465
    }
  ],
  "offerId": 523424397,
  "fromCurrency": "EUR",
  "validSeconds": 20,
  "expirationTime": "2023-09-26T18:02:57.865+00:00"
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
