# Resend Code

`POST` **/v2/mobile/phone/verify/resend**

If the initial verification code for a phone number has not been received or has expired, this API allows users to request a new verification code to be sent to the provided phone number. It is a resend mechanism to ensure users can successfully complete the phone verification process.


## Request

### Headers

- **X-Fingerprint**: string *(required)*
  - Indicates whether fingerprint login has been performed in the application. Fingerprint for WEB for Android and iOS can be viewed [here](https://github.com/crypterium-com/api-vault/wiki/Digital-signature-verification-and-fingerprint).
  - **Default:** `1234444`

- **X-Merchant-ID**: string *(required)*
  - Identification of requests from users of a specific partner.
  - **Default:** `bece038f-2e46-49f4-b25e-89cd38d6dc16`

- **X-Signature**: string
  - Contains a digital signature generated both on the server-side (backend) and the client-side (frontend). It is used for verifying the authenticity of requests. The HMAC_SHA256 algorithm is utilized to generate the signature, employing a shared secret key.


```json
{
  "X-Fingerprint": {
    "type": "string",
    "required": true,
    "description": "Indicates whether fingerprint login has been performed in the application. Fingerprint for WEB for Android and iOS can be viewed [here](https://github.com/crypterium-com/api-vault/wiki/Digital-signature-verification-and-fingerprint).",
    "default": "1234444"
  },
  "X-Merchant-ID": {
    "type": "string",
    "required": true,
    "description": "Identification of requests from users of a specific partner.",
    "default": "bece038f-2e46-49f4-b25e-89cd38d6dc16"
  },
  "X-Signature": {
    "type": "string",
    "description": "Contains a digital signature generated both on the server-side (backend) and the client-side (frontend). It is used for verifying the authenticity of requests. The HMAC_SHA256 algorithm is utilized to generate the signature, employing a shared secret key."
  }
}
```

### Body

**Media Type:** `application/json`

### Parameters

- **phone**: string *(Required)*
  - telephone number, which must be specified during registration.
  
```json
{
  "phone": "+447871234567"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v2/mobile/phone/verify/resend \
  --header 'Accept: application/json' \
  --header 'Content-Type: application/json' \
  --header 'X-Fingerprint: 1234444' \
  --header 'X-Merchant-ID: bece038f-2e46-49f4-b25e-89cd38d6dc16' \
  --header 'X-Signature: ' \
  --data '{
  "phone": "+447871234567"
}'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>

The response status code indicates that the request was successfully processed.

- **Media type:** `application/json`

- **result:** string
  - Response indicating the result of the resend code operation..
  
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
