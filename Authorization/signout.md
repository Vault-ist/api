# SignOut

`POST` **/signout**

The endpoint is intended for user [logout](https://github.com/crypterium-com/api-vault.wiki.git) and invalidation of access tokens. When calling this endpoint, the server should deauthorize the user and invalidate the current access token.


## Request

**Headers**
- **X-DeviceIdD**: string 
  - this header is used for device identification during the sign-out process.

### **Example Headers**

```json
{
  "type": "object",
  "properties": {
    "X-DeviceIdD": {
      "type": "string",
      "description": "This header is used for device identification during the sign-out process."
    }
  }
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://crpt-backend-main-service.sandbox.testessential.net/signout \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI4NTU0ZDc0My05ZDExLTQ5YTEtYTMyMy03YmRmOGQ4NDdjMjEiLCJleHAiOjE3MDk3MjQ1NjQsImlhdCI6MTcwOTYzODE2NH0.deZXGfjS7oVprz2XoZseeYa7l8ti8aAJaELBeDDtglI' \
  --header 'Content-Type: application/json' \
  --header 'X-DeviceId: '
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response indicates a successful sign-out operation.
  
**Media type:** `application/json`
  
- **result:** string
Provides information about the outcome of the registration operation.

  
**Responses example**
```json
{
  "result": "ok"
}
```
</details>


<details>
<summary><strong>400 - Client Error</strong></summary>

Indicates that the server cannot process the request due to a client error.
  
**Media type:** `*/*`
  
  

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
