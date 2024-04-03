# Get Card Details

`POST` **/v2/card/{cardId}/details**

This endpoint is designed for retrieving detailed information about a specific card.

## Request

**Media Type:** `application/json`

### Path Parameters

- **cardId**: *integer<int64>* *(required)*
  - Unique identifier of the card for which the details are being retrieved.

### Body

This endpoint is intended for securely obtaining detailed information about the specified card, including the card number, CVV, expiry date, and cardholder name. The verification code and public key are used for authentication and encryption, respectively, to enhance security during the retrieval process.

The variable `publicKey` can be obtained using the endpoint [GET /v2/card/rsa-public-key](https://github.com/Vault-ist/api/blob/main/Card%20Program%201/Get%20RSA%20Key.md?plain=1).

- **code**: *string* *(required)*
  - A string representing the verification code necessary for accessing card details.
- **publicKey**: *string* *(required)*
  - A string representing the public key used for encryption.

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request GET \
  --url https://api.vault.sandbox.testessential.net/v2/card/7/details/code \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJlOTBmNTNiOC05MTc0LTQyZWUtYTVjNS04ZTA0ZGM2MzA5NWYiLCJleHAiOjE3MTIyMzY0MTAsImlhdCI6MTcxMjE1MDAxMH0.1jyJQ7npbGowVG_AbY3iWQwRv8XepgLx7u2UVyVtMgk'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response provides feedback on the success or failure of the SMS code generation process.
  
**Media type:** `application/json`
  
- **number**: *string*
  - A string representing the card number.
  
- **cvv**: *string*
  - A string representing the card verification value.

- **expiry**: *string*
  - A string representing the card expiry date.
  
- **cardholderName**: *string*
  - A string representing the name of the cardholder.
  
**Responses example**
```json
{
  "cvv": "***",
  "expiry": "12/25",
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
