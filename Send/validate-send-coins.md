# Validate Send Coins Request to Another Wallet

`POST` **/v1/wallet/send/validate**

The endpoint serves the purpose of validating a request to send coins to another wallet before executing the actual transaction.

## Request

### Body

**Media Type:** `application/json`

### Parameters

The API provides functionality for conducting transfers, allowing users to specify either the recipient's `wallet address` or `phone number`.

- **address**: `string` *(required)*
  - Represents the recipient's wallet address.

- **phone**: `string` *(required)*
  - Represents the recipient's phone number.

- **amount**: `integer` *(required)*
  - Represents the amount of coins to be sent.

- **currency**: `string` *(required)*
  - Specifies the currency in which the coins are denoted.

### **Example body**
  
```json
{
  "phone": "+447871236668",
  "amount": 1,
  "currency": "USDT"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v1/wallet/send/validate \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: application/json' \
  --data '{
  "phone": "+447871236668",
  "amount": 1,
  "currency": "USDT"
}'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **possibleToExecute**: `boolean` *(required)*
  - Indicates whether the transaction is possible to execute.
  - **Default:** `true`

- **blockedAmount**: `object` *(required)*
  - Information about any blocked amount.
    - **value**: `integer` *(required)*
      - Numeric value representing the blocked amount.
    - **currency**: `string` *(required)*
      - Currency of the blocked funds.

  
   **Responses example**
```json
{
  "blockedAmount": {
    "value": 0,
    "currency": "EUR" },
  "possibleToExecute": true
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
