# Add Card

`POST` **/v4/payout/card**

The endpoint is designed to facilitate the addition of a new card for payout transactions. It allows users or applications to provide details about a new card to be associated with the payout system.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Request

### Headers

- **X-Sdk-Version**: string *(required)*
  - Interface build version that enables transaction operations.
  - *Example:* payoutCard=1.2

### Body

- **cardNumber**: integer *(required)*
  - An integer representing the card number.

- **cardHolder**: string *(required)*
  - A string representing the name of the cardholder.

- **cardExpirationYear**: integer *(required)*
  - An integer representing the expiration year of the card.

- **cardExpirationMonth**: integer *(required)*
  - An integer representing the expiration month of the card.

```json
{
  "cardHolder": "Mara Sanchez Gonzalez",
  "cardNumber": 4012888888881881,
  "cardExpirationYear": 2026,
  "cardExpirationMonth": 3
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v4/payout/card \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: application/json' \
  --header 'X-Sdk-Version: payoutCard=1.2' \
  --data '{
  "cardHolder": "Mara Sanchez Gonzalez",
  "cardNumber": 4012888888881881,
  "cardExpirationYear": 2026,
  "cardExpirationMonth": 3
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  
200 OK status.

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
