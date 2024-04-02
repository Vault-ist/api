# Get Fiat Rates

`GET` **/v3/payin/fiat-rates**

The endpoint is intended to retrieve information on fiat exchange rates for currency pairs during fiat deposit operations.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
Successful execution of the request to obtain information about KYC limits. This indicates that the server has successfully processed the request, and the returned data contains information about KYC limits.
  
**Media type:** `application/json`

### Body

An array containing exchange rate information for different fiat currencies relative to a base currency.

- **baseCurrency**: string
  - Indicates the base currency for which exchange rate information is provided.
  
- **symbolCurrency**: string
  - Represents the symbol of the fiat currency for which the exchange rate is specified.
  
- **rate**: integer
  - Specifies the current exchange rate between the base currency and the fiat currency.


  
**Responses example**
```json
[
  {
    "rate": 1.669202,
    "baseCurrency": "EUR",
    "symbolCurrency": "AUD"
  },
  {
    "rate": 1,
    "baseCurrency": "EUR",
    "symbolCurrency": "EUR"
  },
  {
    "rate": 0.85524,
    "baseCurrency": "EUR",
    "symbolCurrency": "GBP"
  },
  {
    "rate": 163.351439,
    "baseCurrency": "EUR",
    "symbolCurrency": "JPY"
  },
  {
    "rate": 1448.31831,
    "baseCurrency": "EUR",
    "symbolCurrency": "KRW"
  },
  {
    "rate": 99.460479,
    "baseCurrency": "EUR",
    "symbolCurrency": "RUB"
  },
  {
    "rate": 1.085399,
    "baseCurrency": "EUR",
    "symbolCurrency": "USD"
  }
]
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
