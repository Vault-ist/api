# Limits

`GET` **/v1/kyc/limits**

The endpoint is designed to retrieve information about KYC (Know Your Customer) limits. KYC limits typically define the maximum values or thresholds associated with different KYC levels.

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
Successful execution of the request to obtain information about KYC limits. This indicates that the server has successfully processed the request, and the returned data contains information about KYC limits.
  
**Media type:** `application/json`

### Body

- **kycNoneLimit**
  - **value** (integer): The maximum value or threshold for KYC None.
  - **currency** (string): The currency in which the KYC None limit is defined.

- **kyc0Limit**
  - **value** (integer): The maximum value or threshold for KYC Level 0.
  - **currency** (string): The currency in which the KYC Level 0 limit is defined.

- **kyc1Limit**
  - **value** (integer): The currency in which the KYC Level 1 limit is defined.
    - **Default:** `9700`
  - **currency** (string): The currency in which the KYC Level 1 limit is defined.

- **kyc2Limit**
  - **value** (integer): The currency in which the KYC Level 2 limit is defined.
    - **Default:** `15000`
  - **currency** (string): The currency in which the KYC Level 2 limit is defined.

- **kyc3Limit**
  - **value** (integer): The currency in which the KYC Level 3 limit is defined.
    - **Default:** `32000`
  - **currency** (string): The currency in which the KYC Level 3 limit is defined.

  
**Responses example**
```json
{
  "kyc0Limit": {
    "value": 0,
    "currency": "EUR"
  },
  "kyc1Limit": {
    "value": 9700,
    "currency": "EUR"
  },
  "kyc2Limit": {
    "value": 15000,
    "currency": "EUR"
  },
  "kyc3Limit": {
    "value": 32000,
    "currency": "EUR"
  },
  "kycNoneLimit": {
    "value": 0,
    "currency": "EUR"
  }
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
