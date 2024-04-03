# Create Card Payload Offer

`POST` **/v2/card/{cardId}/payload/offers**

This endpoint is designed to create an offer for a card payload, enabling users to propose a specific currency exchange for a given card.

## Request

### Path Parameters

- **cardId**: *integer<int64>* *(required)*
  - Unique identifier of the card for which the offer is being created.

### Body


This endpoint allows users to suggest a specific currency exchange for a particular card, providing details about the source and target currencies, amount, fees, rate, and expiration time for the offer. Users can create and propose exchange offers for a specific card.

- **fromCurrency**: *string* *(required)*
  - The currency from which the exchange will be initiated.
- **toCurrency**: *string* *(required)*
  - The currency to which the exchange will be made.
- **toAmount**: *integer* *(required)*
  - The amount of the target currency to be received.
- **fromAmount**: *integer* *(required)*
  - The amount of the source currency to be exchanged.


#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v2/card/7/payload/offers \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJlOTBmNTNiOC05MTc0LTQyZWUtYTVjNS04ZTA0ZGM2MzA5NWYiLCJleHAiOjE3MTIyMzY0MTAsImlhdCI6MTcxMjE1MDAxMH0.1jyJQ7npbGowVG_AbY3iWQwRv8XepgLx7u2UVyVtMgk' \
  --header 'Content-Type: application/json' \
  --data '{
  "fromCurrency": "string",
  "toCurrency": "string",
  "toAmount": 0,
  "fromAmount": 0
}'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>

The response status code indicates that the request was successfully processed.

**Media type:** `application/json`

- **offerId**: *integer*
  - Unique identifier of the created offer.
- **expirationTime**: *string*
  - Date and time when the offer expires.
- **from**: *object*
  - Information about the currency and amount of the source currency.
    - **value**: *integer*
      - The amount value.
    - **currency**: *string*
      - Currency.
- **to**: *object*
  - Information about the currency and amount of the target currency.
    - **value**: *integer*
      - The amount value.
    - **currency**: *string*
      - Currency.
- **fees**: *object*
  - Information about transaction fees.
    - **transactionFee**: *integer*
      - Transaction fee.
    - **additionalFee**: *integer*
      - Additional fee.
- **rate**: *object*
  - Exchange rate for the proposed transaction.
    - **value**: *integer*
      - The value of the exchange rate.
    - **currency**: *string*
      - Currency of the exchange rate.
- **possibleToExecute**: *boolean*
  - Boolean value indicating whether the offer can be executed.
- **limit**: *object*
  - Limit for the proposed exchange.
    - **value**: *integer*
      - The value of the limit.
    - **currency**: *string*
      - Currency of the limit.
  
**Responses example**
```json
{
  "offerId": 0,
  "expirationTime": "string",
  "from": {
    "value": 0,
    "currency": "string"
  },
  "to": {
    "value": 0,
    "currency": "string"
  },
  "fees": {
    "transactionFee": 0,
    "additionalFee": 0
  },
  "rate": {
    "value": 0,
    "currency": "string"
  },
  "possibleToExecute": true,
  "limit": {
    "value": 0,
    "currency": "string"
  }
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
