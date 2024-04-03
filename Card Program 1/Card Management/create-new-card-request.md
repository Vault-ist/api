# Create New Card Request

`POST` **/v2/card/card-requests**

The endpoint is intended for initiating the process of creating a new card. This functionality allows users to request the issuance of a new card.

## Request

### Headers

 - **User-Agent**: string *(required)*
    - The string used for identifying the user agent.
    - **Default:** `vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24`

### Body

**Media Type:** `application/json`

### Parameters

- **cardType**: string
  - Specifies the type of the requested card.
- **cardDesignId**: integer
  - Indicates the identifier of the chosen card design for the request.
    - *For cardType VIRTUAL, `"cardDesignId": 4`*

### **Example body**
  
```json
{
  "cardType": "VIRTUAL",
  "cardDesignId": 4
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v2/card/card-requests \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTIyMjQ1MTUsImlhdCI6MTcxMjEzODExNX0.8-moPaoJYz1kexcrOl2XIb3chF2Taf10IJeHEPnCOFI' \
  --header 'Content-Type: application/json' \
  --header 'User-Agent: vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24' \
  --data '{
  "cardType": "VIRTUAL",
  "cardDesignId": 4
}'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
This field indicates the outcome of the cancellation operation.
  
**Media type:** `application/json`
  
- **id**: integer
  - The unique identifier assigned to the request for creating a new card.
  
**Responses example**
```json
{
  "id": 1234
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
