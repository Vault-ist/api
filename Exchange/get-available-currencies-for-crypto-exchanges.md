# Get Available Currencies for Crypto Exchanges

`GET` **/v2/exchange/currencies**

This endpoint serves to provide customers with an overview of the available currency pairs they can trade on the crypto exchange platform, tailored specifically for the current customer.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Request

### Body

**Media Type:** `application/json`

### Query Parameters:
- **coinPairs**: array
  - This parameter allows filtering the output by specified coin pairs.

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request GET \
  --url https://api.vault.sandbox.testessential.net/v2/exchange/currencies \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTIxNTg1MzEsImlhdCI6MTcxMjA3MjEzMX0.KIdck2EPYJ0zyS0W7nA52ilI5t1XG4G4K9134_UTXQA'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>

**Media type:** `application/json`

This response provides detailed information about the available currency pairs for exchange, including exchange rates, minimum and maximum amounts, and other relevant details.

- **pairs**: array
  - An array containing information about currency pairs available for exchange.
    - **exchangePair**: object
      - Detailed information about the exchange pair.
        - **rate**: integer
          - Current exchange rate.
        - **currencyFrom**: string
          - Currency to be exchanged from.
        - **currencyTo**: string
          - Currency to be exchanged to.
        - **minAmountFrom**: integer
          - Minimum amount of currencyFrom.
        - **maxAmountFrom**: integer
          - Maximum amount of currencyFrom.
        - **minAmountTo**: integer
          - Minimum amount of currencyTo.
        - **maxAmountTo**: integer
          - Maximum amount of currencyTo.
        - **amountScaleFrom**: integer
          - Scale of the currencyFrom amount.
        - **amountScaleTo**: integer
          - Scale of the currencyTo amount.
        - **lock**: boolean
          - Indicates if the pair is locked. Default: true.
    - **allAmountFrom**: integer
      - Total amount available of currencyFrom.
    - **rateScale**: integer
      - The scale of the exchange rate.

```json 
{
  "pairs": [
    {
      "lock": false,
      "rate": 1,
      "rateScale": 8,
      "currencyTo": "BITDRIVEN",
      "maxAmountTo": 500,
      "minAmountTo": 1,
      "currencyFrom": "USDT",
      "allAmountFrom": 0,
      "amountScaleTo": 8,
      "maxAmountFrom": 500,
      "minAmountFrom": 1,
      "amountScaleFrom": 8
    }
  ]
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
