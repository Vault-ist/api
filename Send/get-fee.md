# Get Fee

`GET` **/v1/wallet/send/fee/{currency}**

This endpoint is designed to retrieve information about the fee for sending coins.

## Request

### Body

**Media Type:** `application/json`

### Parameters

The API provides functionality for conducting transfers, allowing users to specify either the recipient's `wallet address` or `phone number`.

**Path Parameters:**

- **currency**: `string` *(required)*
  - The currency for which the fee is being requested.
  - Example: `USDT`

**Query Parameters:**

- **amount**: `number` *(required)*
  - The amount to be sent.

- **address**: `string`
  - The wallet address to which the coins will be sent. Always required for send by wallet.

- **customerId**: `integer<int64>`
  - The identifier of the customer for whom the operation is performed.

- **phone**: `string`
  - Recipient's phone number. Needed only for send by phone.


#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request GET \
  --url 'https://api.vault.sandbox.testessential.net/v1/wallet/send/fee/USDT?address=0x9A6034c84cd431409Ac1a35278c7Da36FfDa53E5&amount=10&customerId=74' \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MDk4ODY0MDMsImlhdCI6MTcwOTgwMDAwM30.P81xYvVSC8HhpY-5ycpGT6cgn2K8nXMRD2E2sESfQPY'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **fee**: `integer`
  - The value of the transaction fee.

- **sourceCurrency**: `string`
  - The currency in which the fee is specified.

- **transactionType**: `string`
  - The type of the transaction.

- **transactionAvailability**: `boolean`
  - A flag indicating the availability of the transaction.
  - **Default:** `true`
  
   **Responses example**
```json
{
  "fee": 26.733816,
  "sourceCurrency": "USDT",
  "transactionType": "EXTERNAL",
  "transactionAvailability": false
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
