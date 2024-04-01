# Start

`POST` **/v4/kyc/start**

The endpoint is crafted to commence the KYC1 V4 (Know Your Customer Level 1, version 4) identification process, serving as the first step in customer verification and supplying an identifier for continuous monitoring of KYC1 V4 status or acquiring supplementary details.


## Request

### Query Parameters

- **platform** (string): Types of platforms.
  - *Allowed values:*
    - `COMMON`
    - `WALLETTO`
  - **Default:** `COMMON`


#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url 'https://api.vault.sandbox.testessential.net/v4/kyc/start?platform=COMMON' \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: application/json'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`

- **id** (string): 
   - A unique identifier that can be used for further interaction with the KYC1 V4 process.
  
**Responses example**
```json
{
  "id": "118feeff71324519728"
}
```
</details>


<details>
<summary><strong>400 - Bad Request</strong></summary>

The response status code indicates that the requested page was not found on the server.
  
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
