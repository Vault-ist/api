# Confirm Phone Number

`POST` **/v2/mobile/phone/confirm**

This API is employed to confirm the ownership of a provided phone number during the [account creation process](https://github.com/crypterium-com/api-vault/wiki/Registration-Process). Users may receive a code through SMS or a similar method, and this code needs to be submitted through this API to verify the associated phone number.


## Request

### Headers

- **X-Merchant-ID**: string *(required)*
  - Identification of requests from users of a specific partner.
  - **Default:** `bece038f-2e46-49f4-b25e-89cd38d6dc16`

```json json_schema
{
  "X-Merchant-ID": {
    "type": "string",
    "required": true,
    "description": "Identification of requests from users of a specific partner.",
    "default": "bece038f-2e46-49f4-b25e-89cd38d6dc16"
  }
}
```

### Body

**Media Type:** `application/json`

### Parameters

- **phone**: string *(Required)*
  - telephone number, which must be specified during registration.
- **smsCode**: string *(Required)*
  - SMS containing the necessary code. In this case, the SMS code is always the same, and it is `1234`.
- **fingerprint**: string
  - device fingerprint. Fingerprint for WEB for Android and iOS can be viewed [here](https://github.com/crypterium-com/api-vault/wiki/Digital-signature-verification-and-fingerprint).
  
```json
{
  "phone": "+447871234567",
  "smsCode": "1234",
  "fingerprint": "12344444"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://crpt-backend-main-service.sandbox.testessential.net/v2/mobile/phone/confirm \
  --header 'Accept: application/json' \
  --header 'Authorization: Basic ZG9jOnNlY3JldA==' \
  --header 'Content-Type: application/json' \
  --header 'X-Merchant-ID: bece038f-2e46-49f4-b25e-89cd38d6dc16' \
  --data '{
  "phone": "+447871234567",
  "smsCode": "1234",
  "fingerprint": "12344444"
}'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
Indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **access_token**: string
  - An encrypted key, a short-lived token for accessing a resource.

- **token_type**: string
  - Bearer token.

- **refresh_token**: string
  - These are credentials for accessing the API in the absence of a user session.

- **expires_in**: integer
  - Token lifetime in seconds.

- **scope**: string
  - Token action space. We almost always have read and write permissions.

  
   **Responses example**
```json
{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJmYTdiM2UzNi1jNTQ4LTQ2NjMtYWNiZi00YjAwOWMyYTExZjgiLCJleHAiOjE3MDk4MjE1MjIsImlhdCI6MTcwOTczNTEyMn0.Syx7vEDUcgEQ-pNJSjFQPh35wia3Qy-2u_GyFCSiXgk",
  "token_type": "bearer",
  "refresh_token": "_aUCain3dCLOF4NzSvQbXchMuns",
  "expires_in": 86399,
  "scope": "read write"
}
```
</details>

---

<details>
<summary><strong>400 - Client Error</strong></summary>

Indicates that the server cannot process the request due to a client error.
  
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
