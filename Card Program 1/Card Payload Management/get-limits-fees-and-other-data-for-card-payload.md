# Get Limits, Fees, and Other Data for Card Payload

`GET` **/v2/card/{cardId}/payload/data**

This endpoint is designed to retrieve various data necessary for conducting transactions using a specific card.

## Request

### Path Parameters

- **cardId**: *integer<int64>* *(required)*
  - Unique identifier of the card for which the data is being requested.

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request GET \
  --url https://api.vault.sandbox.testessential.net/v2/card/7/payload/data \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJlOTBmNTNiOC05MTc0LTQyZWUtYTVjNS04ZTA0ZGM2MzA5NWYiLCJleHAiOjE3MTIyMzY0MTAsImlhdCI6MTcxMjE1MDAxMH0.1jyJQ7npbGowVG_AbY3iWQwRv8XepgLx7u2UVyVtMgk'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>

The response status code indicates that the request was successfully processed.

**Media type:** `application/json`

- **card**:
  - **cardId**: *integer*
    - Unique identifier of the card.
  - **maskedPan**: *string*
    - Masked card number.
  - **cardCompany**: *string*
    - Issuing company of the card.
  - **cardBalance**: *object*
    - Information about the card balance.
  - **fees**: *object*
    - Information about fees, including transaction fees and additional fees.
      - **transactionFee**: *integer*
        - Transaction fee.
      - **additionalFee**: *integer*
        - Additional fee.
- **pairs**: *array[object]*
  - Information about currency pairs that can be used for fund exchanges. Each pair contains details about the exchange rate, currencies involved, and limits.
    - **rate**: *integer*
      - Exchange rate.
    - **currencyFrom**: *string*
      - The currency being exchanged.
    - **currencyTo**: *string*
      - The currency to which it is being exchanged.
    - **amountScaleFrom**: *integer*
      - The scale for the amount in the source currency.
    - **amountScaleTo**: *integer*
      - The scale for the amount in the target currency.
    - **fromLimits**: *object*
      - Limits for the currency being exchanged.
        - **min**: *integer*
          - Minimum value.
        - **max**: *integer*
          - Maximum value.
    - **toLimits**: *object*
      - Limits for the target currency being exchanged.
        - **min**: *integer*
          - Minimum value.
        - **max**: *integer*
          - Maximum value.
        - **all**: *integer*
          - Overall limit.
                  
**Responses example**
```json
{
  "card": {
    "cardId": 7,
    "maskedPan": null,
    "cardCompany": "VISA",
    "cardBalance": {
      "value": 0,
      "currency": "EUR"
    }
  },
  "fees": {
    "transactionFee": 0.015,
    "additionalFee": 0.005
  },
  "pairs": [
    {
      "rate": 551.9303482587064,
      "currencyFrom": "BCH",
      "currencyTo": "EUR",
      "amountScaleFrom": 8,
      "amountScaleTo": 8,
      "fromLimits": {
        "min": 1,
        "max": 1.80235387,
        "all": 0
      },
      "toLimits": {
        "min": 552,
        "max": 994,
        "all": null
      }
    },
    {
      "rate": 0.9196716417910448,
      "currencyFrom": "DAI",
      "currencyTo": "EUR",
      "amountScaleFrom": 8,
      "amountScaleTo": 8,
      "fromLimits": {
        "min": 2.17468921,
        "max": 1081.84129388,
        "all": 0
      },
      "toLimits": {
        "min": 2,
        "max": 994,
        "all": null
      }
    },
    {
      "rate": 61163.880597014926,
      "currencyFrom": "BTC",
      "currencyTo": "EUR",
      "amountScaleFrom": 8,
      "amountScaleTo": 8,
      "fromLimits": {
        "min": 1,
        "max": 0.0162667,
        "all": 0
      },
      "toLimits": {
        "min": 61164,
        "max": 994,
        "all": null
      }
    },
    {
      "rate": 3078.855721393035,
      "currencyFrom": "ETH",
      "currencyTo": "EUR",
      "amountScaleFrom": 8,
      "amountScaleTo": 8,
      "fromLimits": {
        "min": 1,
        "max": 0.32281703,
        "all": 0
      },
      "toLimits": {
        "min": 3079,
        "max": 993,
        "all": null
      }
    },
    {
      "rate": 91.96019900497512,
      "currencyFrom": "LTC",
      "currencyTo": "EUR",
      "amountScaleFrom": 8,
      "amountScaleTo": 8,
      "fromLimits": {
        "min": 1,
        "max": 32.44997296,
        "all": 0
      },
      "toLimits": {
        "min": 92,
        "max": 2984,
        "all": null
      }
    },
    {
      "rate": 0.9197014925373135,
      "currencyFrom": "USDC",
      "currencyTo": "EUR",
      "amountScaleFrom": 8,
      "amountScaleTo": 8,
      "fromLimits": {
        "min": 2.17461863,
        "max": 1081.78277802,
        "all": 0
      },
      "toLimits": {
        "min": 2,
        "max": 994,
        "all": null
      }
    },
    {
      "rate": 0.024186655621890547,
      "currencyFrom": "QASH",
      "currencyTo": "EUR",
      "amountScaleFrom": 8,
      "amountScaleTo": 8,
      "fromLimits": {
        "min": 82.69022519,
        "max": 40393.82199113,
        "all": 0
      },
      "toLimits": {
        "min": 2,
        "max": 976,
        "all": null
      }
    },
    {
      "rate": 0.92,
      "currencyFrom": "USDT",
      "currencyTo": "EUR",
      "amountScaleFrom": 8,
      "amountScaleTo": 8,
      "fromLimits": {
        "min": 2.17391304,
        "max": 1081.31487889,
        "all": 0
      },
      "toLimits": {
        "min": 2,
        "max": 994,
        "all": null
      }
    },
    {
      "rate": 0.5384079601990049,
      "currencyFrom": "XRP",
      "currencyTo": "EUR",
      "amountScaleFrom": 8,
      "amountScaleTo": 8,
      "fromLimits": {
        "min": 3.71465533,
        "max": 5545.59402555,
        "all": 0
      },
      "toLimits": {
        "min": 2,
        "max": 2985,
        "all": null
      }
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
