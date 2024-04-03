# Pay Card Order Offer

`POST` **/v2/card/card-requests/payment-offer/{id}/confirm**

The endpoint is designed for confirming the payment of a card order offer.


## Request

**Media Type:** `application/json`

### Path Parameters

- **id**: integer<int64> (*required*)
  - The unique identifier of the card request that needs to be canceled.


#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v2/card/card-requests/payment-offer/1234/confirm \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI0ZGQyYzA2YS01ZTAyLTQ3ZjMtYWM5Zi1hYzE4Y2Q5Y2ZiNDQiLCJleHAiOjE3MTIyMzAyOTIsImlhdCI6MTcxMjE0Mzg5Mn0.Zf1C96fU6YXbxLec3BSjhqZPRpSRLU-rkj5aw2TL7wY' \
  --header 'Content-Type: application/json'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **result**: string
  - A string indicating the result of the payment confirmation process.
  
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
