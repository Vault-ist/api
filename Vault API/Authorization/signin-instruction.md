# Instruction: SignIn

The endpoint is designed for user authentication and obtaining an OAuth access token. Specifically tailored for the client credentials grant type, it generates a token upon successful authentication, enabling secure requests to resources.

### **Required Headers Parameters**:

Use the **X-Merchant-ID** provided to you by your account manager.


```json json_schema
{
  "type": "object",
  "required": ["X-Merchant-ID"],
  "properties": {
    "X-Merchant-ID": {
      "type": "string",
      "required": true,
      "description": "identification of requests from users of a specific partner.",
      "default": "bece038f-2e46-49f4-b25e-89cd38d6dc16"
    }
  }
}
```
### **The body parameters**

```json json_schema
{
  "type": "object",
  "required": ["grant_type"],
  "properties": {
    "password": {
      "type": "string",
      "description": "this is your existing password if you already have an account.",
    },    
    "phone": {
      "type": "string",
      "description": "this is your existing phone number if it's already registered in the system.",
    },
    
    "grant_type": {
      "type": "string",
      "description": "authorization type:`mobile_phone`.",
    }
  }
}

```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl
curl --request POST \
     --url https://api.vault.sandbox.testessential.net/oauth/token \
     --header 'X-Merchant-ID: bece038f-2e46-49f4-b25e-89cd38d6dc16' \
     --header 'accept: application/json' \
     --header 'content-type: application/x-www-form-urlencoded' \
     --data grant_type=mobile_phone \
     --data 'number=+447871239999' \
     --data password=1234Qwerty
```

### **Response Example**

The response status code indicates that the request was successfully processed.

```json

{
  "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MDk4MDQzNjksImlhdCI6MTcwOTcxNzk2OX0.9nA1ur5_fGwlap2mrPN35OhR6dJ0M5qmNLNjJ2iZM6g",
  "token_type": "bearer",
  "refresh_token": "qPMkKwoedBu2lVZzn9-51hkG_vg",
  "expires_in": 86399,
  "scope": "read write",
  "jti": "nejUZ1PeSBnmTtrZdaAj81sQX44"
}

```

