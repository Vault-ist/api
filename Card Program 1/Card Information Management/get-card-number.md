# Get Card Number

`POST` **/v2/card/{cardId}/number**

This endpoint is designed for retrieving the card number associated with a specific card.


## Request

**Media Type:** `application/json`

### Path Parameters

- **cardId**: *integer<int64>* *(required)*
  - Unique identifier of the card for which the card number is being retrieved.

### Body

This endpoint is intended for securely obtaining the card number associated with the specified card. The public key is used for encryption to enhance security during the retrieval process.

The variable `publicKey` can be obtained using the endpoint [GET /v2/card/rsa-public-key](https://github.com/Vault-ist/api/blob/main/Card%20Program%201/Get%20RSA%20Key.md?plain=1).

- **publicKey**: *string* *(required)*
  - A string representing the public key used for encryption.

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v2/card/7/number \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJlOTBmNTNiOC05MTc0LTQyZWUtYTVjNS04ZTA0ZGM2MzA5NWYiLCJleHAiOjE3MTIyMzY0MTAsImlhdCI6MTcxMjE1MDAxMH0.1jyJQ7npbGowVG_AbY3iWQwRv8XepgLx7u2UVyVtMgk' \
  --header 'Content-Type: application/json' \
  --data '{
  "publicKey": "abc123"
}'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **number**: *string* *(required)*
  - A string representing the retrieved card number.

- **cardholderName**: *string* *(required)*
  - A string representing the name of the cardholder.
  
**Responses example**
```json
{
  "number": "**** **** **** 1234",
  "cardholderName": "John Doe"
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
