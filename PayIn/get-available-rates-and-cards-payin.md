# Get Available Rates and Cards Data for PayIn

`GET` **/v3/payin/data**

The endpoint is designed to provide information about available rates and card options for fiat deposits. This endpoint is specifically used to retrieve data related to the process of depositing funds into the system.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
Successful execution of the request to obtain information about KYC limits. This indicates that the server has successfully processed the request, and the returned data contains information about KYC limits.
  
**Media type:** `application/json`

### Body

An array containing exchange rate information for different fiat currencies relative to a base currency.

- **cards**: array[object]
  - Contains information about available cards for payment.
    - **maskedPan**: string
      - Represents the masked PAN (Primary Account Number) of the card.
    - **cardId**: integer
      - Unique identifier for the card.
    - **cardType**: string
      - Indicates the type of the card.
      - Example: `VISA`
    - **minAmountFrom**: integer
      - Minimum amount allowed for payment from the card.
    - **maxAmountFrom**: integer
      - Maximum amount allowed for payment from the card.
    - **validationStatus**: string
      - Indicates the validation status of the card.
    - **billingAddressRequired**: boolean
      - Specifies whether providing a billing address is required for the card.
      - Default: `true`
    - **validTo**: string<date>
      - Represents the expiration date until which the provided data is valid.
      - Match pattern: `YYYY-MM-DDThh:mm:ss<TZDSuffix>`
    - **validSeconds**: integer
      - The number of seconds during which the data remains valid.
    - **pairs**: array[object]
      - Contains information about currency pairs for the pay-in process.
        - **rate**: integer
          - Exchange rate for the currency pair.
        - **currencyFrom**: string
          - The source currency in the pair.
        - **currencyTo**: string
          - The target currency in the pair.
        - **amountScaleFrom**: integer
          - Scale for the amount in the source currency.
        - **amountScaleTo**: integer
          - Scale for the amount in the target currency.
        - **lock**: boolean
          - Whether the currency pair is locked.
    - **fiatPairs**: array[object]
      - Similar to pairs, specifically for fiat currency pairs.
        - **rate**: integer
          - Exchange rate.
        - **currencyFrom**: string
          - Source currency.
        - **currencyTo**: string
          - Target currency.
        - **amountScaleFrom**: integer
          - Scale for the source currency.
        - **amountScaleTo**: integer
          - Scale for the target currency.
        - **lock**: boolean
          - Indicates whether the exchange rate is locked.
          - Default: `true`
    - **feeInfo**: object
      - Information about fees.
        - **name**: string
          - Fee name.
        - **value**: integer
          - Current value of the fee.
        - **valueOld**: integer
          - Previous value of the fee.
        - **includeInRate**: boolean
          - Whether the fee is included in the exchange rate.
    - **feeTable**: array[object]
      - Information about fee percentages based on transaction amounts.
        - **amountFrom**: object
          - Minimum amount for the fee.
          - **value**: integer
            - Amount value.
          - **currency**: string
            - Currency of the amount.
        - **amountTo**: object
          - Maximum amount for the fee.
          - **value**: integer
            - Amount value.
          - **currency**: string
            - Currency of the amount.
        - **percent**: integer
          - Percentage fee.
        - **percentOld**: integer
          - Old percentage fee.
        - **defaultMinAmountFrom**: integer
          - Default minimum deposit amount.
        - **defaultMaxAmountFrom**: integer
          - Default maximum deposit amount.
        - **isFirstPurchase**: boolean
          - Indicates whether it is the user's first purchase.
    - **freeTransactionsPromo**: object
      - Details about a promotional offer for free transactions.
        - **available**: integer
          - Available free transactions.
        - **total**: integer
          - Total free transactions.
    - **fees**: object
      - Details about various fees.
        - **currency**: string
          - Fee currency.
        - **scale**: integer
          - Fee scale.
        - **rate**: integer
          - Fee rate.
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
          - Indicates whether fee table is enabled.
    - **feeTable**: array[object]
      - Fee details in tabular form.
        - **amountFrom**: object
          - **value**: integer
            - Amount value.
          - **currency**: string
            - Currency of the amount.
        - **amountTo**: object
          - **value**: integer
            - Amount value.
          - **currency**: string
            - Currency of the amount.
        - **percent**: integer
          - Percentage fee.
    - **billingAddressRequired**: boolean
      - Specifies whether providing a billing address is generally required for pay-in transactions.

  
**Responses example**
```json
{
  "fees": {
    "rate": 0,
    "scale": 8,
    "currency": "EUR",
    "feeTable": null,
    "partnerFee": 0,
    "insuranceFee": null,
    "additionalFee": 0,
    "crypteriumGas": 0,
    "transactionFee": 0,
    "feeTableEnabled": false
  },
  "cards": [
    {
      "cardId": 127,
      "cardType": "VISA",
      "maskedPan": "4907***3896",
      "maxAmountFrom": 0,
      "minAmountFrom": 0,
      "validationStatus": "APPROVED",
      "billingAddressRequired": false
    },
    {
      "cardId": 289,
      "cardType": "MASTERCARD",
      "maskedPan": "5570***2778",
      "maxAmountFrom": 0,
      "minAmountFrom": 0,
      "validationStatus": "APPROVED",
      "billingAddressRequired": true
    },
    {
      "cardId": 999,
      "cardType": "MASTERCARD",
      "maskedPan": "5232***7382",
      "maxAmountFrom": 0,
      "minAmountFrom": 0,
      "validationStatus": "APPROVED",
      "billingAddressRequired": true
    },
    {
      "cardId": 150,
      "cardType": "VISA",
      "maskedPan": "4012***1881",
      "maxAmountFrom": 0,
      "minAmountFrom": 0,
      "validationStatus": "APPROVED",
      "billingAddressRequired": false
    }
  ],
  "pairs": [
    {
      "lock": false,
      "rate": 1.0948105977665863,
      "currencyTo": "USDC",
      "currencyFrom": "EUR",
      "amountScaleTo": 8,
      "amountScaleFrom": 8
    },
    {
      "lock": false,
      "rate": 1.0944511327569224,
      "currencyTo": "USDT",
      "currencyFrom": "EUR",
      "amountScaleTo": 8,
      "amountScaleFrom": 8
    },
    {
      "lock": false,
      "rate": 0.002547446185199337,
      "currencyTo": "BCH",
      "currencyFrom": "EUR",
      "amountScaleTo": 8,
      "amountScaleFrom": 8
    },
    {
      "lock": false,
      "rate": 1.5528673695979627,
      "currencyTo": "XRP",
      "currencyFrom": "EUR",
      "amountScaleTo": 8,
      "amountScaleFrom": 8
    },
    {
      "lock": false,
      "rate": 39.055459185559094,
      "currencyTo": "QASH",
      "currencyFrom": "EUR",
      "amountScaleTo": 8,
      "amountScaleFrom": 8
    },
    {
      "lock": false,
      "rate": 0.000271749468729788,
      "currencyTo": "ETH",
      "currencyFrom": "EUR",
      "amountScaleTo": 8,
      "amountScaleFrom": 8
    },
    {
      "lock": false,
      "rate": 0.011021712774165105,
      "currencyTo": "LTC",
      "currencyFrom": "EUR",
      "amountScaleTo": 8,
      "amountScaleFrom": 8
    },
    {
      "lock": false,
      "rate": 1.0952782554407947,
      "currencyTo": "DAI",
      "currencyFrom": "EUR",
      "amountScaleTo": 8,
      "amountScaleFrom": 8
    },
    {
      "lock": false,
      "rate": 0.000015174161437903,
      "currencyTo": "BTC",
      "currencyFrom": "EUR",
      "amountScaleTo": 8,
      "amountScaleFrom": 8
    }
  ],
  "feeInfo": null,
  "validTo": "2024-03-12T07:33:20.498+00:00",
  "feeTable": null,
  "fiatPairs": [],
  "validSeconds": 30,
  "firstPurchase": false,
  "firstPurchaseLimit": {
    "value": 0,
    "currency": "EUR"
  },
  "defaultMaxAmountFrom": 0,
  "defaultMinAmountFrom": 0,
  "freeTransactionsPromo": {
    "total": 0,
    "available": 0
  },
  "billingAddressRequired": true
}
```
</details>


<details>
<summary><strong>400 - Bad Request</strong></summary>

The response status code indicates that the requested page was not found on the server.
  
- **Media type:** `application/json`
  

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
