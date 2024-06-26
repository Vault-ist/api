# Update Status of Push Notifications

`PUT` **/v1/customer/device/push**

This endpoint is used to enable or disable push notifications on a specific device. It is generated by the user when toggling the push notification settings within the application.

Additionally, it is used after receiving permission for push notifications in iOS (system popup).

## Request

### Headers


- **User-Agent**: string (*Required*)
  - User identifier making the request.  
  - **Default**: `vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24c`


```json 
{
  "User-Agent": {
    "description": "User identifier making the request.",
    "type": "string",
    "required": true,
    "default": "vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24c"
  }
}
```

### Body

**Media Type:** `application/json`

### Parameters

- **state**: string
  - Indicates the desired state of push notifications.
  - Allowed values:
    - `ENABLED`: In this state, push notifications are allowed on the device.
    - `DISABLED`: In this state, push notifications are disabled on the device.

- **deviceToken**: string
  - A unique identifier for the device.

- **deviceId**: string
  - Identifier for the specific device.
  
### **Example body**

```json 
{
  "state": "ENABLED",
  "deviceId": "device123",
  "deviceToken": "abc123xyz456"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request PUT \
  --url https://api.vault.sandbox.testessential.net/v1/customer/device/push \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: application/json' \
  --header 'User-Agent: vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24c' \
  --data '{
  "state": "ENABLED",
  "deviceId": "device123",
  "deviceToken": "abc123xyz456"
}'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `*/*`
  
- **result:** string
  - A string indicating the result of the operation.
  
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
