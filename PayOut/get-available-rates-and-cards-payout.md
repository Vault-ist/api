# Get Available Rates and Cards Data for PayOut

`GET` **/v4/payout/data**

The endpoint is designed to provide information about available rates, cards, and fees for payout transactions. It allows users to retrieve data related to currency exchange rates, available cards for payouts, and associated transaction fees.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Request

### Headers

- **X-Sdk-Version**: string *(required)*
  - Interface build version that enables transaction operations.
  - *Example:* payoutCard=1.2

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request GET \
  --url https://api.vault.sandbox.testessential.net/v4/payout/data \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'X-Sdk-Version: payoutCard=1.2'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  
200 OK status.
  
**Media type:** `application/json`

 - *cards*: array[object]
    - Information about supported cards.
      - *maskedPan*: string
        - Masked PAN (Primary Account Number) of the card.
      - *cardId*: integer
        - Identifier for the card.
      - *cardType*: string
        - Type of the card.
  
  - *pairsLimits*: array[object]
    - Limits associated with currency pairs.
      - *currencyFrom*: string
        - Currency from which the transaction is made.
      - *currencyTo*: string
        - Currency to which the transaction is made.
      - *minAmountFrom*: integer
        - Minimum amount allowed for the transaction.
      - *maxAmountFrom*: integer
        - Maximum amount allowed for the transaction.
      - *allAmountFrom*: integer
        - Overall limit for all transactions.
      - *validationStatus*: string
        - Validation status of the card.
  
  - *validSeconds*: integer
    - An integer representing the validity period in seconds.
  
  - *pairs*: array[object]
    - Information about currency pairs and associated rates.
      - *rate*: integer
        - Exchange rate between the specified currency pair.
      - *currencyFrom*: string
        - Currency from which the conversion is made.
      - *currencyTo*: string
        - Currency to which the conversion is made.
      - *amountScaleFrom*: integer
        - Scale for the amount in the source currency.
      - *amountScaleTo*: integer
        - Scale for the amount in the target currency.
      - *defaultMinAmountFrom*: integer
        - Default minimum amount for the transaction.
      - *defaultMaxAmountFrom*: integer
        - Default maximum amount for the transaction.
      - *defaultMaxAmountAll*: integer
        - Default overall limit for all transactions.
  
  - *fees*: object
    - Details about fees associated with the payout.
      - *rate*: integer
        - Fee rate.
      - *transactionFee*: integer
        - Transaction fee.
      - *additionalFee*: integer
        - Additional fee.
      - *crypteriumGas*: integer
        - Gas fee related to Crypterium.
      - *partnerFee*: integer
        - Partner fee.
      - *fixFee*: integer
        - Fixed fee.

```json 
{
  "fees": {
    "rate": 0.02,
    "fixFee": 2.5,
    "partnerFee": 0,
    "additionalFee": 0,
    "crypteriumGas": 0,
    "transactionFee": 0.035
  },
  "cards": [
    {
      "cardId": 7,
      "cardType": "VISA",
      "maskedPan": "4907***3896",
      "pairsLimits": [
        {
          "currencyTo": "EUR",
          "currencyFrom": "BCH",
          "allAmountFrom": 0,
          "maxAmountFrom": 5.18931567,
          "minAmountFrom": 0.05503819
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "DAI",
          "allAmountFrom": 0,
          "maxAmountFrom": 2210.97182484,
          "minAmountFrom": 23.44970117
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "BTC",
          "allAmountFrom": 0.03070239,
          "maxAmountFrom": 0.03070239,
          "minAmountFrom": 0.00032563
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "ETH",
          "allAmountFrom": 0,
          "maxAmountFrom": 0.55148465,
          "minAmountFrom": 0.00584907
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "LTC",
          "allAmountFrom": 3.83108331,
          "maxAmountFrom": 22.59206265,
          "minAmountFrom": 0.23961278
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "USDC",
          "allAmountFrom": 0,
          "maxAmountFrom": 2209.78690065,
          "minAmountFrom": 23.43713379
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "USDT",
          "allAmountFrom": 1927.26686346,
          "maxAmountFrom": 2209.06206348,
          "minAmountFrom": 23.42944612
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "XRP",
          "allAmountFrom": 0,
          "maxAmountFrom": 3174.29678905,
          "minAmountFrom": 33.66678412
        }
      ],
      "validationStatus": "APPROVED"
    },
    {
      "cardId": 8,
      "cardType": "MASTERCARD",
      "maskedPan": "5570***2778",
      "pairsLimits": [
        {
          "currencyTo": "EUR",
          "currencyFrom": "BCH",
          "allAmountFrom": 0,
          "maxAmountFrom": 5.18931567,
          "minAmountFrom": 0.05503819
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "DAI",
          "allAmountFrom": 0,
          "maxAmountFrom": 2210.97182484,
          "minAmountFrom": 23.44970117
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "BTC",
          "allAmountFrom": 0.03070239,
          "maxAmountFrom": 0.03070239,
          "minAmountFrom": 0.00032563
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "ETH",
          "allAmountFrom": 0,
          "maxAmountFrom": 0.55148465,
          "minAmountFrom": 0.00584907
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "LTC",
          "allAmountFrom": 3.83108331,
          "maxAmountFrom": 22.59206265,
          "minAmountFrom": 0.23961278
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "USDC",
          "allAmountFrom": 0,
          "maxAmountFrom": 2209.78690065,
          "minAmountFrom": 23.43713379
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "USDT",
          "allAmountFrom": 1927.26686346,
          "maxAmountFrom": 2209.06206348,
          "minAmountFrom": 23.42944612
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "XRP",
          "allAmountFrom": 0,
          "maxAmountFrom": 3174.29678905,
          "minAmountFrom": 33.66678412
        }
      ],
      "validationStatus": "APPROVED"
    },
    {
      "cardId": 9,
      "cardType": "MASTERCARD",
      "maskedPan": "5232***7382",
      "pairsLimits": [
        {
          "currencyTo": "EUR",
          "currencyFrom": "BCH",
          "allAmountFrom": 0,
          "maxAmountFrom": 5.18931567,
          "minAmountFrom": 0.05503819
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "DAI",
          "allAmountFrom": 0,
          "maxAmountFrom": 2210.97182484,
          "minAmountFrom": 23.44970117
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "BTC",
          "allAmountFrom": 0.03070239,
          "maxAmountFrom": 0.03070239,
          "minAmountFrom": 0.00032563
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "ETH",
          "allAmountFrom": 0,
          "maxAmountFrom": 0.55148465,
          "minAmountFrom": 0.00584907
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "LTC",
          "allAmountFrom": 3.83108331,
          "maxAmountFrom": 22.59206265,
          "minAmountFrom": 0.23961278
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "USDC",
          "allAmountFrom": 0,
          "maxAmountFrom": 2209.78690065,
          "minAmountFrom": 23.43713379
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "USDT",
          "allAmountFrom": 1927.26686346,
          "maxAmountFrom": 2209.06206348,
          "minAmountFrom": 23.42944612
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "XRP",
          "allAmountFrom": 0,
          "maxAmountFrom": 3174.29678905,
          "minAmountFrom": 33.66678412
        }
      ],
      "validationStatus": "APPROVED"
    },
    {
      "cardId": 15,
      "cardType": "VISA",
      "maskedPan": "4012***1881",
      "pairsLimits": [
        {
          "currencyTo": "EUR",
          "currencyFrom": "BCH",
          "allAmountFrom": 0,
          "maxAmountFrom": 5.18931567,
          "minAmountFrom": 0.05503819
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "DAI",
          "allAmountFrom": 0,
          "maxAmountFrom": 2210.97182484,
          "minAmountFrom": 23.44970117
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "BTC",
          "allAmountFrom": 0.03070239,
          "maxAmountFrom": 0.03070239,
          "minAmountFrom": 0.00032563
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "ETH",
          "allAmountFrom": 0,
          "maxAmountFrom": 0.55148465,
          "minAmountFrom": 0.00584907
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "LTC",
          "allAmountFrom": 3.83108331,
          "maxAmountFrom": 22.59206265,
          "minAmountFrom": 0.23961278
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "USDC",
          "allAmountFrom": 0,
          "maxAmountFrom": 2209.78690065,
          "minAmountFrom": 23.43713379
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "USDT",
          "allAmountFrom": 1927.26686346,
          "maxAmountFrom": 2209.06206348,
          "minAmountFrom": 23.42944612
        },
        {
          "currencyTo": "EUR",
          "currencyFrom": "XRP",
          "allAmountFrom": 0,
          "maxAmountFrom": 3174.29678905,
          "minAmountFrom": 33.66678412
        }
      ],
      "validationStatus": "APPROVED"
    }
  ],
  "pairs": [
    {
      "rate": 381.5532,
      "currencyTo": "EUR",
      "currencyFrom": "BCH",
      "amountScaleTo": 8,
      "amountScaleFrom": 8,
      "defaultMaxAmountAll": 0,
      "defaultMaxAmountFrom": 5.18931567,
      "defaultMinAmountFrom": 0.05503819
    },
    {
      "rate": 0.8955338,
      "currencyTo": "EUR",
      "currencyFrom": "DAI",
      "amountScaleTo": 8,
      "amountScaleFrom": 8,
      "defaultMaxAmountAll": 0,
      "defaultMaxAmountFrom": 2210.97182484,
      "defaultMinAmountFrom": 23.44970117
    },
    {
      "rate": 64490.076,
      "currencyTo": "EUR",
      "currencyFrom": "BTC",
      "amountScaleTo": 8,
      "amountScaleFrom": 8,
      "defaultMaxAmountAll": 0.03070239,
      "defaultMaxAmountFrom": 0.03070239,
      "defaultMinAmountFrom": 0.00032563
    },
    {
      "rate": 3590.3084,
      "currencyTo": "EUR",
      "currencyFrom": "ETH",
      "amountScaleTo": 8,
      "amountScaleFrom": 8,
      "defaultMaxAmountAll": 0,
      "defaultMaxAmountFrom": 0.55148465,
      "defaultMinAmountFrom": 0.00584907
    },
    {
      "rate": 87.6414,
      "currencyTo": "EUR",
      "currencyFrom": "LTC",
      "amountScaleTo": 8,
      "amountScaleFrom": 8,
      "defaultMaxAmountAll": 3.83108331,
      "defaultMaxAmountFrom": 22.59206265,
      "defaultMinAmountFrom": 0.23961278
    },
    {
      "rate": 0.896014,
      "currencyTo": "EUR",
      "currencyFrom": "USDC",
      "amountScaleTo": 8,
      "amountScaleFrom": 8,
      "defaultMaxAmountAll": 0,
      "defaultMaxAmountFrom": 2209.78690065,
      "defaultMinAmountFrom": 23.43713379
    },
    {
      "rate": 0.896308,
      "currencyTo": "EUR",
      "currencyFrom": "USDT",
      "amountScaleTo": 8,
      "amountScaleFrom": 8,
      "defaultMaxAmountAll": 1927.26686346,
      "defaultMaxAmountFrom": 2209.06206348,
      "defaultMinAmountFrom": 23.42944612
    },
    {
      "rate": 0.6237602,
      "currencyTo": "EUR",
      "currencyFrom": "XRP",
      "amountScaleTo": 8,
      "amountScaleFrom": 8,
      "defaultMaxAmountAll": 0,
      "defaultMaxAmountFrom": 3174.29678905,
      "defaultMinAmountFrom": 33.66678412
    }
  ],
  "validSeconds": 30
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
