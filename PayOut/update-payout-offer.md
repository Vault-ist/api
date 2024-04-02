# Update PayOut Offer

`PUT` **/v4/payout/offer/{offerId}**

The endpoint is designed to update a payout offer by modifying certain parameters. Users or applications can use this endpoint to make adjustments to an existing payout offer.

It allows you to adjust the offer details without affecting the client's funds.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Request

**Media Type:** `application/json`

### **Path Parameters**
- **offerId**: string *(required)*
  - Identifier of the payout offer to be updated.

### **Headers**
- **X-Sdk-Version**: string *(required)*
  - Interface build version that enables transaction operations.
  - *Example*: payoutCard=1.2

### **Body**
- **amount**: integer *(required)*
  - An integer representing the updated amount for the payout offer.
- **fromCurrency**: string *(required)*
  - A string representing the updated source currency for the payout offer.
- **toCurrency**: string *(required)*
  - A string representing the updated target currency for the payout offer.
    
### **Example body**
```json
{
  "amount": 55.47614851,
  "toCurrency": "EUR",
  "fromCurrency": "USDT"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request PUT \
  --url https://api.vault.sandbox.testessential.net/v4/payout/offer/4323 \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTIxNTg1MzEsImlhdCI6MTcxMjA3MjEzMX0.KIdck2EPYJ0zyS0W7nA52ilI5t1XG4G4K9134_UTXQA' \
  --header 'Content-Type: application/json' \
  --header 'X-Sdk-Version: payoutCard=1.2' \
  --data '{
  "amount": 55.47614851,
  "toCurrency": "EUR",
  "fromCurrency": "USDT"
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>

**Media Type:** `application/json`
  
- **offerId**: integer
  - Identifier of the updated payout offer.
- **validSeconds**: integer
  - Indicates the validity period of the updated offer in seconds.
- **amount**: integer
  - The updated amount specified in the offer.
- **currencyFrom**: string
  - The updated source currency of the offer.
- **amountTo**: integer
  - The updated converted amount in the target currency.
- **currencyTo**: string
  - The updated target currency of the offer.
- **rate**: integer
  - The updated exchange rate used for the conversion.
- **feeInfo**: array[object]
  - An array containing information about fees associated with the updated offer.
    - **currency**: string
      - The currency in which the fee is applicable.
    - **name**: string
      - The name of the fee.
    - **scale**: integer
      - The scale of the fee.
    - **value**: integer
      - The value of the fee.
    - **type**: string
      - The type of fee.
- **possibleToExecute**: boolean
  - A boolean indicating whether it is possible to execute the updated payout offer.
- **limit**: object
  - An object specifying any limit associated with the updated offer.
    - **value**: integer
      - The updated value of the limit.
    - **currency**: string
      - The updated currency of the limit.


```json 
{
  "offerId": 9098,
  "validSeconds": 20,
  "amount": 55.47614851,
  "currencyFrom": "USDT",
  "amountTo": 50.55008842690604,
  "currencyTo": "EUR",
  "rate": 0.911204,
  "feeInfo": [
    {
      "currency": "USDT",
      "name": "Transaction fee",
      "scale": 8,
      "value": 4.63070466785,
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
