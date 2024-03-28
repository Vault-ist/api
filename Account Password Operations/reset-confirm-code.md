# Check SMS Code for New Password

`POST` **/v2/mobile/password/reset/confirm/code**

The endpoint is used for checking the SMS code associated with the [process of resetting a password](https://github.com/crypterium-com/api-vault/wiki/Password-Reset-Process) for a mobile device. 

> 🚧 Before using this endpoint, it is recommended to first request a password reset using the endpoint [POST /v2/mobile/password/reset](https://github.com/crypterium-com/api-vault/blob/main/Account%20Password%20Operations/resend-password.md).This endpoint provides the ability to reset a user's password.

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

  
### **Example body**

```json 
{
  "code": "1234",
  "phone": "+447871234567"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://crpt-backend-main-service.sandbox.testessential.net/v2/mobile/password/reset/confirm/code \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJmYTdiM2UzNi1jNTQ4LTQ2NjMtYWNiZi00YjAwOWMyYTExZjgiLCJleHAiOjE3MDk4MTkxNTAsImlhdCI6MTcwOTczMjc1MH0.3xszxc2SaOTZm6-r7h_zRXU6_aQhgdRxMGUUDq9rXxI' \
  --header 'Content-Type: application/json' \
  --header 'X-Merchant-ID: bece038f-2e46-49f4-b25e-89cd38d6dc16' \
  --header 'X-Version: 1.2' \
  --data '{
  "code": "1234",
  "phone": "+447871234567"
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **result:** string
  - confirms the success of the password reset confirmation.
  
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
