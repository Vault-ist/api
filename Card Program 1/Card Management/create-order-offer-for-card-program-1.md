# Create Order Offer for Card Program 1

`POST` **/v2/card/card-requests/{id}/payment-offer/{currency}**

This endpoint is designed to create a card order offer for Card Program 1. The client can specify the card request identifier `id`, choose the currency of the offer `currency`, and use the User-Agent header for user identification.

## Request

### Path Parameters

- **currency**: string *(required)*
  - The currency in which the card order is being offered.

- **id**: integer<int64> *(required)*
  - The unique identifier of the card request that needs to be canceled.

### Headers

- **User-Agent**: string *(required)*
  - User identifier making the request.
  - **Default:** `vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24`

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v2/card/card-requests/1234/payment-offer/LTC \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI0ZGQyYzA2YS01ZTAyLTQ3ZjMtYWM5Zi1hYzE4Y2Q5Y2ZiNDQiLCJleHAiOjE3MTIyMzAyOTIsImlhdCI6MTcxMjE0Mzg5Mn0.Zf1C96fU6YXbxLec3BSjhqZPRpSRLU-rkj5aw2TL7wY' \
  --header 'Content-Type: application/json' \
  --header 'User-Agent: vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>

The response status code indicates that the request was successfully processed.

**Media type:** `application/json`

- **offerId**: integer
  - Unique identifier of the card order offer.

- **cryptoPrice**: object
  - Information about the price in cryptocurrency.
    - **value**: integer
      - Price value.
    - **currency**: string
      - Currency in which the price is specified.
  
- **id**: integer
  - The unique identifier assigned to the request for creating a new card.
  
**Responses example**
```json
{
  "offerId": 98765,
  "cryptoPrice": {
    "value": 0.005,
    "currency": "BTC"
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
