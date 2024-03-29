# Send Coins to Another Wallet

`POST` **/v1/wallet/send**

This endpoint is designed for sending coins to another wallet. It performs the transaction of transferring coins from one wallet to another.

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

- **fee**: `integer` *(required)*
  - A number representing the transaction fee.

### **Example body**
  
```json
{
  "fee": 16.714556,
  "amount": 10,
  "address": "0x9A6034c84cd431409Ac1a35278c7Da36FfDa53E5",
  "currency": "USDT"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v1/wallet/send \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: application/json' \
  --data '{
  "fee": 16.714556,
  "amount": 10,
  "address": "0x9A6034c84cd431409Ac1a35278c7Da36FfDa53E5",
  "currency": "USDT"
}'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  

- **txId**: `string`
  - A string representing a unique identifier for the transaction.

- **sequenceId**: `string`
  - A string representing a unique identifier for the transaction sequence.

- **fee**: `integer`
  - A number representing the transaction fee.

- **internal**: `boolean`
  - A boolean indicating whether the transaction is internal or external.
    - **`true`**: Internal transfer to the phone number or wallet that our user has.
    - **`false`**: External transfer and this transaction goes to the blockchain.
  - **Default:** `true`

- **sendConfirmation**: `boolean`
  - A boolean indicating whether the send confirmation was successful.
  - **Default:** `true`

  
   **Responses example**
```json
{
  "fee": 132.1,
  "txId": "70edc783-59a6-43cf-a44a-f95007cac0ce",
  "internal": true,
  "sequenceId": "fea1901e-171e-4789-8183-e990dd0d627b",
  "sendConfirmation": false
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
