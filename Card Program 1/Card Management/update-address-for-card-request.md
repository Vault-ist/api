# Update Address for Card Request

`PUT` **/v2/card/card-requests/{cardRequestId}/address**

The endpoint is designed to update the address information in a card request with the specified identifier.

## Request

**Media type**: `application/json`

### Path Parameters

- **cardRequestId**: integer<int64> *(required)*
  - The unique identifier of the card request that needs to be updated.

### Headers

- **User-Agent**: string<int64> *(required)*
  - User identifier making the request.
  - *Default*: `vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24`

### Body


- **country**: string *(required)*
  - The country associated with the updated address information.

- **documentCountry**: string *(required)*
  - The country as specified in relevant documents.

- **city**: string *(required)*
  - The city of the updated address.

- **state**: string *(required)*
  - The state or region associated with the updated address.

- **address**: string *(required)*
  - The full address details, including street, house/apartment number, etc.

- **postalCode**: string *(required)*
  - The postal code associated with the updated address.

### **Example body**
  
```json
{
  "country": "string",
  "documentCountry": "string",
  "city": "string",
  "state": "string",
  "address": "string",
  "postalCode": "string"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request PUT \
  --url https://api.vault.sandbox.testessential.net/v2/card/card-requests/cardRequestId/address \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI0ZGQyYzA2YS01ZTAyLTQ3ZjMtYWM5Zi1hYzE4Y2Q5Y2ZiNDQiLCJleHAiOjE3MTIyMzAyOTIsImlhdCI6MTcxMjE0Mzg5Mn0.Zf1C96fU6YXbxLec3BSjhqZPRpSRLU-rkj5aw2TL7wY' \
  --header 'Content-Type: application/json' \
  --header 'User-Agent : vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24' \
  --data '{
  "country": "string",
  "documentCountry": "string",
  "city": "string",
  "state": "string",
  "address": "string",
  "postalCode": "string"
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>

The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **result**: string
  - A string indicating the result.
  
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
