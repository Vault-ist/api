# Set New Password

`POST` **/v2/mobile/password/reset/confirm**

The endpoint is designed for setting a new password after confirming the [password reset](https://github.com/crypterium-com/api-vault/wiki/Password-Reset-Process) for a mobile device.

>Before using this endpoint, it is recommended to first request a password reset using the endpoint [POST /v2/mobile/password/reset](https://github.com/crypterium-com/api-vault/blob/main/Account%20Password%20Operations/resend-password.md). This endpoint provides the ability to reset a user's password. 
>After requesting a password reset, the request should be confirmed using an SMS code through the endpoint [POST /v2/mobile/password/reset/confirm/code](https://github.com/crypterium-com/api-vault/blob/main/Account%20Password%20Operations/reset-confirm-code.md).This endpoint is used to verify the SMS code associated with the password reset process for a mobile device.

## Request

### Headers

- **X-Version**: string *(required)*
  - Version fingerprint.
  - **Default:** `1.2`

- **X-Merchant-ID**: string *(required)*
  - Identification of requests from users of a specific partner.


```json 
{
  "X-Version": {
    "type": "string",
    "required": true,
    "description": "Version fingerprint.",
    "default": "1.2"
  },
  "X-Merchant-ID": {
    "type": "string",
    "required": true,
    "description": "Identification of requests from users of a specific partner."
  }
}
```

### Body

**Media Type:** `application/json`

### Parameters

- **Media Type:** application/json

  - **code**: string
    - The confirmation code sent to the client to verify the password reset request. In this case, the SMS code is always the same, and it is `1234`.
  
  - **phone**: string
    - The phone number that needs to be provided during registration.

 - **password**: string
    - The new password that the client wants to set.

  
### **Example body**

```json 
{
  "code": "1234",
  "phone": "+447871234567",
  "password": "12345Qwerty1234"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://crpt-backend-main-service.sandbox.testessential.net/v2/mobile/password/reset/confirm \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJmYTdiM2UzNi1jNTQ4LTQ2NjMtYWNiZi00YjAwOWMyYTExZjgiLCJleHAiOjE3MDk4MTAyNTgsImlhdCI6MTcwOTcyMzg1OH0.LMBg43_P2sHTb17mSdysXfSMWaOBPCiLcXUdC3heQ6A' \
  --header 'Content-Type: application/json' \
  --header 'X-Merchant-ID: bece038f-2e46-49f4-b25e-89cd38d6dc16' \
  --header 'X-Version: 1.2' \
  --data ' {
  "code": "1234",
  "phone": "+447873214567",
  "password": "1234Qwerty1234"
}'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
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
