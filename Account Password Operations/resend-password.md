# Change Password

`POST` **/v2/mobile/password/reset**

The endpoint provides the ability to [reset a user's password](https://github.com/crypterium-com/api-vault/wiki/Password-Reset-Process), usually by sending instructions to the registered mobile number.

## Request

### Headers

- **X-Merchant-ID**: string *(required)*
  - Identification of requests from users of a specific partner.
  - **Default:** `bece038f-2e46-49f4-b25e-89cd38d6dc16`

- **X-Version**: string *(required)*
  - Version fingerprint.
  - **Default:** `1.2`

- **X-Fingerprint**: string
  - Indicates whether fingerprint login has been performed in the application. Fingerprint for WEB for Android and iOS can be viewed [here](link).

- **X-Signature**: string
  - A signature that verifies the data between the sender and the recipient. More information about X-Signature can be found [here](link).


```json 
{
  "X-Merchant-ID": {
    "type": "string",
    "required": true,
    "description": "Identification of requests from users of a specific partner.",
    "default": "bece038f-2e46-49f4-b25e-89cd38d6dc16"
  },
  "X-Version": {
    "type": "string",
    "required": true,
    "description": "Version fingerprint.",
    "default": "1.2"
  },
  "X-Fingerprint": {
    "type": "string",
    "description": "Indicates whether fingerprint login has been performed in the application. Fingerprint for WEB for Android and iOS can be viewed [here]."
  },
  "X-Signature": {
    "type": "string",
    "description": "A signature that verifies the data between the sender and the recipient. More information about X-Signature can be found [here]."
  }
}
```

### Body

**Media Type:** `application/json`

### Parameters

- **phone**: string (*Required*)
  - The phone number needed for registration.
  
### **Example body**

```json 
{
  "phone": "+447871234567"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://crpt-backend-main-service.sandbox.testessential.net/v2/mobile/password/reset \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJmYTdiM2UzNi1jNTQ4LTQ2NjMtYWNiZi00YjAwOWMyYTExZjgiLCJleHAiOjE3MDk4MTkxNTAsImlhdCI6MTcwOTczMjc1MH0.3xszxc2SaOTZm6-r7h_zRXU6_aQhgdRxMGUUDq9rXxI' \
  --header 'Content-Type: application/json' \
  --header 'X-Fingerprint: ' \
  --header 'X-Merchant-ID: bece038f-2e46-49f4-b25e-89cd38d6dc16' \
  --header 'X-Signature: ' \
  --header 'X-Version: 1.2' \
  --data '{
  "phone": "+447871234567"
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **result:** string
  - The response status code indicates successful re-sending of the email to the mailbox.
  
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

<details>
<summary><strong>403 - Account Duplication (Phone Number Uniqueness Check)</strong></summary>
  
Errors related to account duplication and phone number uniqueness check.
 
If a user attempts to register with a phone number already in the database, they will not receive an error message during the waiting period for SMS confirmation. This is a security measure to prevent unauthorized access to accounts.
</details>
