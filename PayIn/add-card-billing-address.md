# Add Card Billing Address

`POST` **/v3/payin/card/{cardId}/billing-address**

The endpoint is crucial for adding a billing address to a card, enhancing security measures, validating the user's identity, and ensuring up-to-date cardholder information.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Request

### Path Parameters
- **cardId**: integer `<int64>` *(required)*
  - Unique identifier of the card for which billing address information needs to be added or updated.

### Body

Media Type: `application/json`

- **address**: string *(required)*
  - The street address associated with the card's billing information.
- **city**: string *(required)*
  - The city associated with the card's billing information.
- **countryCode**: string *(required)*
  - Country code of the cardholder in ISO-3166 format.
- **zip**: string *(required)*
  - The postal code (ZIP code) associated with the card's billing information.
- **state**: string *(required)*
  - The state or region associated with the card's billing information.

```json json_schema
{
  "zip": "L6P2454",
  "city": "Brampton ",
  "address": "17 mellowood Ave",
  "countryCode": "CA"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v3/payin/card/23/billing-address \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: application/json' \
  --data '{
  "zip": "L6P2454",
  "city": "Brampton ",
  "address": "17 mellowood Ave",
  "countryCode": "CA"
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  
200 OK status, indicating that the card's billing address has been added successfully.
  
**Media type:** `application/json`
  
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
