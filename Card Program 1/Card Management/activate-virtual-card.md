# Activate Virtual Card

`POST` **/v2/card/virtual/activate**

This endpoint facilitates the activation of virtual cards programmatically using a unique key identifier and activation code. Once activated, the virtual card can be utilized for online transactions and other operations.


## Request

### Body

**Media Type:** `application/json`

### Parameters

The variable `keyId` can be obtained using the endpoint [GET /v2/card/rsa-public-key](https://github.com/Vault-ist/api/blob/main/Card%20Program%201/Get%20RSA%20Key.md).

- **keyId**: *string*
  - A unique identifier for the key used in the activation process.

- **passCode**: *string*
  - The activation code required to activate the virtual card.

### **Example body**
  
```json
{
  "keyId": "abc123def456",
  "passCode": "a1b2c3"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v2/card/virtual/activate \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJlOTBmNTNiOC05MTc0LTQyZWUtYTVjNS04ZTA0ZGM2MzA5NWYiLCJleHAiOjE3MTIyMzY0MTAsImlhdCI6MTcxMjE1MDAxMH0.1jyJQ7npbGowVG_AbY3iWQwRv8XepgLx7u2UVyVtMgk' \
  --header 'Content-Type: application/json' \
  --data '{
  "keyId": "abc123def456",
  "passCode": "a1b2c3"
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **id**: *integer*
  - Unique identifier of the activated card.
- **expired**: *string*
  - The expiration date and time of the activated card.
  - *Match pattern*: `YYYY-MM-DDThh:mm:ss<TZDSuffix>`
- **number**: *string*
  - The number of the activated virtual card.
- **balance**: *object*
  - Contains information about the balance of the virtual card.
    - **value**: *integer*
      - The balance value.
    - **currency**: *string*
      - The currency in which the balance is represented.
- **cardholderName**: *string*
  - The name of the cardholder associated with the activated virtual card.
- **cardType**: *string*
  - Type of the card.
  - *Example*: `COLLECTION`
- **cardCompany**: *string*
  - The company that issued the activated virtual card.
  - *Example*: `VISA`
- **monthlyIncome**: *object*
  - Contains information about the monthly income associated with the activated virtual card.
    - **value**: *integer*
      - The monthly income value.
    - **currency**: *string*
      - The currency in which the monthly income is represented.
- **monthlyExpenses**: *object*
  - Contains information about the monthly expenses associated with the activated virtual card.
    - **value**: *integer*
      - The monthly expenses value.
    - **currency**: *string*
      - The currency in which the monthly expenses are represented.
- **cardRequestId**: *integer*
  - Unique identifier for the virtual card request associated with the activation.
- **additionalStatuses**: *array[string]*
  - Additional statuses related to the activated virtual card.
  
**Responses example**
```json
{
  "id": 987654,
  "number": "1234-5678-9876-5432",
  "status": "COLLECTION",
  "balance": {
    "value": 5000,
    "currency": "USD"
  },
  "expired": "2024-01-26T10:11:30.696Z",
  "cardType": "VIRTUAL",
  "cardCompany": "VISA",
  "cardRequestId": 123456,
  "monthlyIncome": {
    "value": 6000,
    "currency": "USD"
  },
  "cardholderName": "John Doe",
  "monthlyExpenses": {
    "value": 1000,
    "currency": "USD"
  },
  "additionalStatuses": [
    "ADDRESS"
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
