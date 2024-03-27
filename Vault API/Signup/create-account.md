# Registration of a new user

This endpoint is designed for [registering] a new user in a mobile application or service using a phone number as the primary identifier.

> ❗️ When re-registering in the system, it is necessary to use a new phone number that has not been used before.

User registration involves providing necessary information such as the phone number and chosen password.

### **Required Headers Parameters и Body Parameters**:

Use the **X-Merchant-ID** provided to you by your account manager.

```json json_schema
{
  "type": "object",
  "required": ["X-Merchant-ID", "X-Version"],
  "properties": {
    "X-Merchant-ID": {
      "type": "string",
      "required": true,
      "description": "identification of requests from users of a specific partner.",
      "default": "bece038f-2e46-49f4-b25e-89cd38d6dc16"
    },
    "X-Version": {
      "type": "string",
      "required": true,
      "description": "version fingerprint.",
      "default": "1.2"
    }
  }
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
     --url https://api.vault.sandbox.testessential.net/v2/mobile/signup \
     --header 'X-Merchant-ID: bece038f-2e46-49f4-b25e-89cd38d6dc16' \
     --header 'X-Version: 1.2' \
     --header 'accept: application/json' \
     --header 'content-type: application/json' \
     --data '
{
  "phone": "+447871234567",
  "password": "1234Qwerty",
  "analyticsCallback": "string"
}
'
```

After entering the phone number and password into the respective fields, you need to click the `Try It!` button.

This action initiates the process of sending data to the server and receiving a response from the API using the provided credentials.

### **Response Example**

The response status code indicates that the request was successfully processed.

```json

{
  "result": "ok"
}
```
