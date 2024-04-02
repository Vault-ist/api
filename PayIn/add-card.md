# Add Card

`POST` **/v3/payin/card**

The endpoint is a part of a system designed for managing credit or debit card information within a platform. Its primary function is to allow users to add a new card to their account, facilitating the deposit of funds associated with that specific card into the platform.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Request

### Body

**Media Type:** `application/json`

- **cardNumber**: integer *(required)*
  - The number of the new card, typically found on the front side of the card.

- **cardHolder**: string *(required)*
  - The name of the cardholder, matching the one indicated on the card itself.

- **cardExpirationYear**: integer *(required)*
  - The year the card expires.

- **cardExpirationMonth**: integer *(required)*
  - The month the card expires (1 to 12).

- **billingAddress**: object *(required)*
  - Information about the billing address for the card.
  - **address**: string *(required)*
    - The street address and house number of the cardholder.
  - **city**: string *(required)*
    - The city of the cardholder.
  - **countryCode**: string *(required)*
    - The country code of the cardholder in ISO-3166 format.
  - **zip**: string *(required)*
    - The postal code of the cardholder.
  - **state**: string *(required)*
    - The region or state of the cardholder.


```json json_schema
{
  "cardHolder": "Mara Sanchez Gonzalez",
  "cardNumber": 4012888888881881,
  "billingAddress": {
    "zip": "8700",
    "city": "tielt",
    "state": null,
    "address": "kasteelstraat 79",
    "countryCode": "BE"
  },
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v3/payin/card \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: application/json' \
  --data '{
  "cardHolder": "Mara Sanchez Gonzalez",
  "cardNumber": 4012888888881881,
  "billingAddress": {
    "zip": "8700",
    "city": "tielt",
    "state": null,
    "address": "kasteelstraat 79",
    "countryCode": "BE"
  },
  "cardExpirationYear": 2026,
  "cardExpirationMonth": 3
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
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
