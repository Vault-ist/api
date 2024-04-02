# Update Existing Offer Without Charging Customer

`PUT` **/v3/payin/offer/{offerId}**

The request is designed to update an existing offer without charging the customer. This request is useful when you need to modify the parameters of an existing offer, such as the amount, currencies, or expiration date, before the client agrees and completes the actual payment transaction.

It allows you to adjust the offer details without affecting the client's funds.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Request

**Media Type:** `application/json`

### Path Parameters
- **offerId**: string *(required)*
  - Unique identifier of the offer that needs to be updated.

### Body
- **amount**: integer *(required)*
  - The updated amount for the offer.
- **fromCurrency**: string *(required)*
  - The updated currency from which the operation is conducted.
- **toAmount**: integer *(required)*
  - The updated amount that the customer is expected to deposit as a result of the operation.
- **toCurrency**: string *(required)*
  - The updated currency to which the operation is applied.
- **operation**: string
  - The type of operation.
  - *Example*: `PAYIN`
- **insuranceOrderRequest**: object
  - Updated information about insurance for the operation.
  - **baseAsset**: string
    - The updated primary asset for insurance.
  - **expiryDate**: string
    - The updated expiration date of the insurance offer.
  - **linkedPrice**: integer
    - The updated linked price for insurance.
  - **linkedPriceCurrency**: string
    - The updated currency of the linked price for insurance.

### **Example body**
```json 
{
  "amount": 117.99,
  "toAmount": 120.24616516,
  "operation": "PAYIN",
  "toCurrency": "USDT",
  "fromCurrency": "EUR"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request PUT \
  --url https://api.vault.sandbox.testessential.net/v3/payin/offer/12345 \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: application/json' \
  --data '{
  "amount": 117.99,
  "toAmount": 120.24616516,
  "operation": "PAYIN",
  "toCurrency": "USDT",
  "fromCurrency": "EUR"
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>

**Media Type:** `application/json`
  
- **offerId**: `integer`
  - The unique identifier of the updated offer.
- **expirationTime**: `string<date-time>`
  - The time when the updated offer expires. In ISO 8601 format.
  - *Match pattern*: `YYYY-MM-DDThh:mm:ss<TZDSuffix>`
- **validSeconds**: `integer`
  - The number of seconds during which the updated offer is valid.
- **fromCurrency**: `string`
  - The updated currency of the operation.
- **rate**: `object`
  - Updated information about the exchange rate.
  - **rate**: `integer`
    - The updated exchange rate.
  - **currency**: `string`
    - The updated currency for the exchange.
- **commissionFix**: `integer`
  - Updated fixed commission.
- **commissionPercentage**: `integer`
  - Updated percentage commission.
- **minCrypto**: `integer`
  - Updated minimum amount in cryptocurrency.
- **maxCrypto**: `integer`
  - Updated maximum amount in cryptocurrency.
- **feeInfo**: `array[object]`
  - Updated information about fees.
  - **name**: `string`
    - The name of the updated fee.
  - **value**: `integer`
    - Fee value. It should be a positive numeric value.
  - **valueOld**: `integer`
    - Old fee value. It should be a positive numeric value.
  - **scale**: `integer`
    - Scale of the fee. It should be a positive numeric value.
  - **currency**: `string`
    - Currency of the fee. It should be a three-letter currency code.
- **limit**: `object`
  - The updated limit of the operation.
  - **value**: `integer`
    - The limit value. It should be a positive numeric value.
  - **currency**: `string`
    - The currency of the limit. It should be a three-letter currency code.
- **fees**: `object`
  - Updated detailed information about fees associated with the operation.
  - **currency**: `string`
    - The currency of fees. It should be a three-letter currency code.
  - **scale**: `integer`
    - Scale of fees. It should be a positive numeric value.
  - **rate**: `integer`
    - Rate of fees. It should be a positive numeric value.
  - **partnerFee**: `integer`
    - Partner fee. It should be a positive numeric value.
  - **crypteriumGas**: `integer`
    - Crypterium gas fee. It should be a positive numeric value.
  - **additionalFee**: `integer`
    - Additional fee. It should be a positive numeric value.
  - **transactionFee**: `integer`
    - Transaction fee. It should be a positive numeric value.
  - **insuranceFee**: `integer`
    - Insurance fee. It should be a positive numeric value.
- **feeTableEnabled**: `boolean`
  - Indicates if the fee table is enabled.
  - *Default*: `true`
- **feeTable**: `array[object]`
  - Updated information about fee percentages based on transaction amounts.


```json 
{
  "offerId": 7402,
  "expirationTime": "2024-03-12T07:57:40.844+00:00",
  "validSeconds": 20,
  "fromCurrency": "EUR",
  "rate": {
    "rate": 1.0662729658792651,
    "currency": "EUR",
    "commissionFix": 0,
    "commissionPercentage": 0,
    "minCrypto": 0,
    "maxCrypto": 0
  },
  "feeInfo": [
    {
      "name": "Crypterium gas",
      "value": 0.155,
      "valueOld": 0.155,
      "scale": 8,
      "currency": "EUR"
    },
    {
      "name": "Additional Fee",
      "value": 0.155,
      "valueOld": 0.155,
      "scale": 8,
      "currency": "EUR"
    },
    {
      "name": "Transaction fee",
      "value": 0.93,
      "valueOld": 0.93,
      "scale": 8,
      "currency": "EUR"
    }
  ],
  "fees": {
    "currency": "EUR",
    "scale": 8,
    "rate": 0.025,
    "partnerFee": 0,
    "crypteriumGas": 0.005,
    "additionalFee": 0.005,
    "transactionFee": 0.03,
    "insuranceFee": null,
    "feeTableEnabled": false,
    "feeTable": null
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
