---
title: "SignIn"
slug: "signin-instruction"
excerpt: "The endpoint is intended for user authentication and obtaining an OAuth access token."
hidden: false
createdAt: "Thu Mar 21 2024 06:21:49 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Fri Mar 22 2024 06:20:09 GMT+0000 (Coordinated Universal Time)"
---
Specifically tailored for the client credentials grant type, it generates a token upon successful authentication, enabling secure requests to resources.

### **Required Headers Parameters и Body Parameters**:

Use the **X-Merchant-ID** provided to you by your account manager.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/d9ed576-image.png",
        null,
        ""
      ],
      "align": "center"
    }
  ]
}
[/block]


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

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/8660435-image.png",
        null,
        ""
      ],
      "align": "center"
    }
  ]
}
[/block]


After entering the phone number and password into the respective fields, you need to click the `Try It!` button.

This action initiates the process of sending data to the server and receiving a response from the API using the provided credentials.

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

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0dcc41c-logo.png",
        "",
        "logo"
      ],
      "align": "right"
    }
  ]
}
[/block]
