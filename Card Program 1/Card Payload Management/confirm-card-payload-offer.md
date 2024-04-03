# Confirm Card Payload Offer

`POST` **/v2/card/{cardId}/payload/offers/{offerId}/confirm**

This API endpoint is designed for confirming a card payload offer associated with a specific card and offer.

## Request

### Path Parameters

- **cardId**: *integer<int64>* *(required)*
  - Unique identifier of the card for which the payload offer is being created and confirmed.

- **offerId**: *integer<int64>* *(required)*
  - Unique identifier of the payload offer that needs to be created and confirmed.


#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v2/card/7/payload/offers/3423525/confirm \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJlOTBmNTNiOC05MTc0LTQyZWUtYTVjNS04ZTA0ZGM2MzA5NWYiLCJleHAiOjE3MTIyMzY0MTAsImlhdCI6MTcxMjE1MDAxMH0.1jyJQ7npbGowVG_AbY3iWQwRv8XepgLx7u2UVyVtMgk' \
  --header 'Content-Type: application/json'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>

The response status code indicates that the request was successfully processed.

**Media type:** `application/json`

- **cardNumber**: *string*
  - The card number for which the payload offer is created and confirmed.

- **amount**: *object*
  - An object representing the amount associated with the offer, including the value and currency.
    - **value**: *integer*
      - The value of the offer amount.
    - **currency**: *string*
      - The currency of the offer amount.

- **status**: *string*
  - A string indicating the status of the confirmation process.
    - **Example**: `PENDING`

  
**Responses example**
```json
{
  "cardNumber": "string",
  "amount": {
    "value": 0,
    "currency": "string"
  },
  "status": "PENDING"
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
