# Execute Offer Exchange

`PUT` **/v1/mobile/exchange/offer/{offerId}**

The endpoint is designed for executing an existing currency exchange offer within a mobile application.

> 📘 This endpoint is accessible for `KYC_0` level and higher.

## Request

**Media Type:** `application/json`

### Path Parameters
- **offerId**: integer<int64> *(required)*
  - Unique identifier of the exchange offer.



```json 
{
  "cardCVV": "***",
  "fingerprint": {
    "acceptContent": "text/html,application/xhtml+x0.8",
    "browserLanguage": "en-us",
    "browserColorDepth": 32,
    "browserJavaEnabled": false,
    "browserScreenWidth": 428,
    "browserAcceptHeader": "text/html,applicat+xm=0.8",
    "browserScreenHeight": 884,
    "browserJavascriptEnabled": true
  }
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request PUT \
  --url https://api.vault.sandbox.testessential.net/v1/mobile/exchange/offer/9098 \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTIxNTg1MzEsImlhdCI6MTcxMjA3MjEzMX0.KIdck2EPYJ0zyS0W7nA52ilI5t1XG4G4K9134_UTXQA' \
  --header 'Content-Type: application/json'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  

- **offerId**: integer
  - Unique identifier of the exchange offer.

- **status**: string
  - Execution status of the offer.

```json 
{
  "status": "SUCCESS",
  "offerId": 5543253425482
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
