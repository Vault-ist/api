---
title: "Digital signature verification and fingerprint"
slug: "digital-signature-verification-and-fingerprint"
excerpt: "The verification of the digital signature and fingerprint will occur in two new headers, `x-signature` and `x-fingerprint` respectively."
hidden: true
createdAt: "Wed Mar 20 2024 11:00:52 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 20 2024 16:45:15 GMT+0000 (Coordinated Universal Time)"
---
This process is specifically relevant for endpoints associated with authentication and registration, which do not necessitate an access token. These endpoints include:

- Create account [POST /v2/mobile/signup](https://vault-bxou.readme.io/reference/create-account)
- Resend Code [POST /v2/mobile/phone/verify/resend](https://vault-bxou.readme.io/reference/resend-code)
- Resend password [POST /v2/mobile/password/reset](https://vault-bxou.readme.io/reference/resend-password)

<h2>X-signature</h2>

The content of the x-signature header is generated independently by both the backend and frontend. At the time of sending the request, the content of the header sent by the frontend is compared with what is available on the backend. If they match, the request is successful.

### **Components of the signature**:

```json json_schema
{
  "type": "object",
  "properties": {
    "seed": {
      "type": "string",
      "description": "a string computed in a certain way."
    },
    "phone": {
      "type": "string",
      "description": "the user's phone number (present in all requests)."
    },
    "fingerprint": {
      "type": "string",
      "description": "computed differently for each platform (iOS, Android, WEB). An example of the fingerprint from the frontend is described [here](Api/fingerprint.json)."
    },
    "password": {
      "type": "string",
      "description": "the user's password if applicable (in practice, only in the registration request)."
    }
  }
}
```

The signature is computed by applying the `HMAC_SHA256` algorithm (using a shared secret) to a string composed of the aforementioned components.

### **The computation of seed occurs using the following variables**

```json json_schema
{
  "type": "object",
  "properties": {
    "seedString": {
      "type": "string",
      "description": "a generated sequence of random characters known to both the frontend and backend."
    },
    "seedOffset": {
      "type": "integer",
      "description": "computed from known parameters. Takes the last digit of the sum of all digits of the phone number as **seedOffset**."
    },
    "seedLength": {
      "type": "integer",
      "description": "the length of the seed. In our case, a preset value is used."
    },
    "seed": {
      "type": "string",
      "description": "computed substring of seedString based on seedOffset and seedLength."
    },
    "phone": {
      "type": "string",
      "description": "the user's phone number (present in all requests)."
    },
    "fingerprint": {
      "type": "string",
      "description": "computed differently for each platform (iOS, Android, WEB). An example of the fingerprint from the frontend is described [here](Api/fingerprint.json)."
    },
    "password": {
      "type": "string",
      "description": "the user's password if applicable (in practice, only in the registration request)."
    }
  },
  
}
```

### **Example of signature computation**

```python
fingerprint = myOwnFingerprint
password = 12345
phone = 700000031
seedOffset = (7+3+1) % 10 = 1
seedLength = 4
seedString = abcdefghijklmn
seed = substring(abcdefghijklmn, 1, 4) = bcde
```

`signature = hmacSha256(seed+myOwnFingerprint+phone+password) = hmacSha256(bcdemyOnwFingerprint70000003112345)`

<h2>X-fingerprint</h2>

These variables provide information about the user's browser and device characteristics, which can be used to create a unique fingerprint.

- `timezone`: User's timezone (number).
- `browserColorDepth`: Color depth of the browser in bits (number).
- `browserLanguage`: Language of the user's browser (string).
- `browserScreenHeight`: Height of the browser screen in pixels (number).
- `browserScreenWidth`: Width of the browser screen in pixels (number).
- `browsertz`: Refresh rate of the browser screen in Hertz (number).
- `os`: Operating system of the user (string).
- `userAgent`: User agent string in the HTTP header "User-Agent" (string).
- `browserJavaEnabled`: Whether Java is enabled in the browser (boolean).
- `browserJavascriptEnabled`: Whether JavaScript is enabled in the browser (boolean).

Example fingerprint for WEB on Android and iOS:

```json
{
  "timezone": "number",
  "browserColorDepth": "number",
  "browserLanguage": "string",
  "browserScreenHeight": "number",
  "browserScreenWidth": "number",
  "browsertz": "number",
  "os": "string",
  "userAgent": "string",
  "browserJavaEnabled": "boolean",
  "browserJavascriptEnabled": "boolean"
}

```
```Text Example 1
{
  "timezone": 3,
  "browserColorDepth": 24,
  "browserLanguage": "en-US",
  "browserScreenHeight": 1080,
  "browserScreenWidth": 1920,
  "browsertz": 3000,
  "os": "Windows 10",
  "userAgent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36",
  "browserJavaEnabled": false,
  "browserJavascriptEnabled": true
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
