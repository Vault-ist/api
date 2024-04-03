# Get Customer for Card Program 1 prices

`GET` **/v2/card/prices**

This endpoint serves the purpose of providing customers with information about the prices associated with Card Program 1.

The User-Agent header helps in identifying the user making the request.

## Request

### Headers

- **User-Agent**: string *(required)*
  - User identifier making the request.
  - **Default:** `vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24`

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request GET \
  --url https://api.vault.sandbox.testessential.net/v2/card/prices \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTIyMjQ1MTUsImlhdCI6MTcxMjEzODExNX0.8-moPaoJYz1kexcrOl2XIb3chF2Taf10IJeHEPnCOFI' \
  --header 'User-Agent: vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response includes details about the cost of different types of cards, potential delivery charges, and the available card designs.
  
**Media type:** `application/json`

- **prices**: array[object]
  - An array containing objects representing card prices.
    - **cardType**: string
      - Type of the card.
      - **Example**: `PLASTIC`
    - **currency**: string
      - Currency in which the price is specified.
    - **price**: integer
      - The price of the card.
    - **delivery**: integer
      - The delivery cost associated with the card.
    - **cardDesignIds**: array[integer]
      - Identifiers of available card designs.

**Responses example**
```json
{
  "prices": [
    {
      "price": 0,
      "cardType": "PLASTIC",
      "currency": "USD",
      "delivery": 0,
      "cardDesignIds": [
        1,
        2,
        3
      ]
    },
    {
      "price": 10,
      "cardType": "WALETTO_CARD",
      "currency": "USD",
      "delivery": 5,
      "cardDesignIds": [
        4,
        5,
        6
      ]
    }
  ]
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
