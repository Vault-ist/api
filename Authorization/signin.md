# Confirm Phone Number

`POST` **/v2/mobile/phone/confirm**

The endpoint is designed for user authentication and obtaining an OAuth access token. Specifically tailored for the client credentials grant type, it generates a token upon successful authentication, enabling secure requests to resources.


## Request

**Headers**
- **X-Merchant-ID**: string (required)
  - Identification of requests from users of a specific partner.
  - Default: `bece038f-2e46-49f4-b25e-89cd38d6dc16`

### **Example Headers**

```json
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

**Content Type**: application/x-www-form-urlencoded

### Parameters

  - **password**: string
    - Password required for registration.
  - **number**: string
    - Phone number transmitted during token acquisition.
  - **grant_type**: string (required)
    - Authorization type: `mobile_phone`

### **Example Body**
  
```json
{
  "password": "1234Qwerty ",
  "number": "+447871239999",
  "grant_type": "mobile_phone"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/oauth/token \
  --header 'Accept: application/json' \
  --header 'Content-Type: application/x-www-form-urlencoded' \
  --header 'X-Merchant-ID: bece038f-2e46-49f4-b25e-89cd38d6dc16' \
  --data 'password=+447871239999' \
  --data number=1234Qwerty \
  --data grant_type=mobile_phone
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


<details>
<summary><strong>400 - Client Error</strong></summary>

Indicates that the server cannot process the request due to a client error.
  
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
