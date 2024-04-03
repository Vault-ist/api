# Set Passcode to Card Program 1

`POST` **/v2/card/{id}/passcode/code/set**

This endpoint enables users to establish or update a passcode for enhanced security on their Card Program 1 card. The passcode is a vital element in authorizing various card-related transactions.

## Request

**Media Type:** `application/json`

### Path Parameters


- **id**: *integer<int64>* *(required)*
  - Unique identifier of the card for which the passcode is being set.


### Body

The variable `keyId` can be obtained using the endpoint [GET /v2/card/rsa-public-key](https://github.com/Vault-ist/api/blob/main/Card%20Program%201/Get%20RSA%20Key.md).

- **keyId**: *string* *(required)*
  - Identifier associated with the passcode setting operation.

- **code**: *string* *(required)*
  - A security code or authorization token required to initiate the passcode setting.

- **passCode**: *string* *(required)*
  - The new passcode to be set on the Card Program 1 card.

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v2/card/1234435/passcode/code/set \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJlOTBmNTNiOC05MTc0LTQyZWUtYTVjNS04ZTA0ZGM2MzA5NWYiLCJleHAiOjE3MTIyMzY0MTAsImlhdCI6MTcxMjE1MDAxMH0.1jyJQ7npbGowVG_AbY3iWQwRv8XepgLx7u2UVyVtMgk' \
  --header 'Content-Type: application/json' \
  --data '{
  "code": "1234",
  "keyId": "abc123",
  "passCode": "pass123"
}'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **result**: *string*
  - A string representing the result of the operation. This could indicate the success or failure of the passcode setting.
  
**Responses example**
```json
{
  "result": "ok"
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
