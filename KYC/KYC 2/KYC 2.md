# KYC 2

`POST` **/v1/kyc/upload/document**

The endpoint is used to upload documents as part of the KYC (Know Your Customer) Level 2 identity verification process, transmitting information about the required documents to confirm a user's identity.

The process of completing KYC 2 can be read [here](https://github.com/Vault-ist/api/wiki/KYC-Procedure).

## Request

### Query Parameters

- **docType**: string *(required)*
  - The type of the uploaded document.
  - *Allowed values:*
    - `PASSPORT_FRONT`
    - `DRIVING_LICENCE_FRONT`
    - `ID_CARD_FRONT`
    - `PASSPORT_BACK`
    - `DRIVING_LICENCE_BACK`
    - `ID_CARD_BACK`
    - `SELFIE`
    - `UTILITY_BILL`
    - `BANK_STATEMENT`
    - `CREDIT_CARD_STATEMENT`
    - `GOVERNMENT_CORRESPONDENCE`
    - `VIDEO_VERIFICATION`

### Body

- **Content Type**: `multipart/form-data`

- **image**: string *(required)*
  - The request body containing the document image in the $binary format.


#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url 'https://api.vault.sandbox.testessential.net/v1/kyc/upload/document?docType=PASSPORT_FRONT' \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: multipart/form-data' \
  --form 'image =@437b2d8-image.png'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`

- **result**: string
  - Represents the upload of a document image.
  
**Responses example**
```json
{
  "result": "ok"
}
```
</details>


<details>
<summary><strong>400 - Bad Request</strong></summary>

The response status code indicates that the server cannot or will not process the request due to something perceived as a client error.
  
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
