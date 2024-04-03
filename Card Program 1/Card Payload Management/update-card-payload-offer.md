# Update Card Payload Offer

`PUT` **/v2/card/{cardId}/payload/offers/{offerId}**

This endpoint is designed to update an existing card payload offer, allowing users to modify the details of a previously created offer.

> ❗️ To keep the offer up-to-date, it should be refreshed every **30 seconds**.

## Request

### Path Parameters

- **cardId**: *integer<int64>* *(required)*
  - Unique identifier of the card associated with the offer.

- **offerId**: *integer<int64>* *(required)*
  - Unique identifier of the offer to be updated.


### Body

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
curl --request PUT \
  --url https://api.vault.sandbox.testessential.net/v2/card/7/payload/offers/3423525 \
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
  - The identifier of the updated offer.
- **expirationTime**: *string*
  - The date and time when the offer will expire.
- **from**: *object*
  - Details about the funds being sent.
    - **value**: *integer*
      - The numerical value of the sent funds.
    - **currency**: *string*
      - The currency of the sent funds.
- **to**: *object*
  - Details about the recipient's funds.
    - **value**: *integer*
      - The numerical value of the recipient's funds.
    - **currency**: *string*
      - The currency of the recipient's funds.
- **fees**: *object*
  - Information about fees associated with the transaction.
    - **transactionFee**: *integer*
      - The fee charged for the transaction.
    - **additionalFee**: *integer*
      - Any additional fees.
- **rate**: *object*
  - Exchange rate details.
    - **value**: *integer*
      - The numerical value of the exchange rate.
    - **currency**: *string*
      - The currency in which the exchange rate is expressed.
- **possibleToExecute**: *boolean*
  - Indicates whether it is possible to execute the offer.
- **limit**: *object*
  - Details about any limits associated with the offer.
    - **value**: *integer*
      - The numerical value of the limit.
    - **currency**: *string*
      - The currency in which the limit is expressed.

  
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
