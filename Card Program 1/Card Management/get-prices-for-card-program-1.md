# Get Card Price

`GET` **/v2/card/card-requests/{id}/price/{currency}**

This endpoint provides detailed pricing information for a specific card request, catering to both fiat and cryptocurrency currencies. Additionally, it includes specific details related to the card, delivery, and the associated delivery address.


## Request

**Media Type:** `application/json`

### Path Parameters

- **currency**: *string* *(required)*
  - The currency code for which pricing details are requested.

- **id**: *integer<int64>* *(required)*
  - Unique identifier of the card request.

### Headers

- **User-Agent**: *string* *(required)*
  - User identifier making the request.
  - Default: `vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24c`


#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request GET \
  --url https://api.vault.sandbox.testessential.net/v2/card/card-requests/123321/price/2134 \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJlOTBmNTNiOC05MTc0LTQyZWUtYTVjNS04ZTA0ZGM2MzA5NWYiLCJleHAiOjE3MTIyMzY0MTAsImlhdCI6MTcxMjE1MDAxMH0.1jyJQ7npbGowVG_AbY3iWQwRv8XepgLx7u2UVyVtMgk' \
  --header 'User-Agent: vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24c'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **fiatPrice**: *object*
  - **value**: *integer*
    - Value of the price in fiat currency.
  - **currency**: *string*
    - Currency code for the price in fiat currency.
- **cryptoPrice**: *object*
  - **value**: *integer*
    - Value of the price in cryptocurrency.
  - **currency**: *string*
    - Currency code for the price in cryptocurrency.
- **card**: *object*
  - **fiat**: *object*
    - **value**: *object*
      - Value in fiat currency for the card.
  - **crypto**: *object*
    - **value**: *object*
      - Value in cryptocurrency for the card.
- **delivery**: *object*
  - **fiat**: *object*
    - Information about the price associated with delivery.
  - **crypto**: *object*
    - Currency code for the price in cryptocurrency.
- **address**: *object*
  - **country**: *string*
    - Information about the delivery address.
  - **city**: *string*
    - Country of delivery.
  - **state**: *string*
    - State/region of delivery.
  - **address**: *string*
    - Actual delivery address.
  - **postalCode**: *string*
    - Postal code of delivery.
   
      
**Responses example**
```json
{
  "fiatPrice": {
    "value": 0,
    "currency": "string"
  },
  "cryptoPrice": {
    "value": 0,
    "currency": "string"
  },
  "card": {
    "fiat": {
      "value": 0,
      "currency": "string"
    },
    "crypto": {
      "value": 0,
      "currency": "string"
    }
  },
  "delivery": {
    "fiat": {
      "value": 0,
      "currency": "string"
    },
    "crypto": {
      "value": 0,
      "currency": "string"
    }
  },
  "address": {
    "country": "string",
    "city": "string",
    "state": "string",
    "address": "string",
    "postalCode": "string"
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
