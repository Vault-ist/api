# Get RSA Key

`GET` **/v2/card/rsa-public-key**

This endpoint is designed to retrieve the RSA public key, which is used for encrypting data when performing other requests listed below:

- [POST /v2/card/virtual/activate](Api/Card-Program-1.yaml/paths/~1v2~1card~1virtual~1activate/post)
- [POST /v2/card/{cardId}/details](Api/Card-Program-1.yaml/paths/~1v2~1card~1{cardId}~1details/post)
- [POST /v2/card/{id}/passcode/code/set](Api/Card-Program-1.yaml/paths/~1v2~1card~1{id}~1passcode~1code~1set/post)


#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request GET \
  --url https://api.vault.sandbox.testessential.net/v2/card/rsa-public-key \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTIxNTg1MzEsImlhdCI6MTcxMjA3MjEzMX0.KIdck2EPYJ0zyS0W7nA52ilI5t1XG4G4K9134_UTXQA'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **id**: string
  - Unique identifier for the RSA key.
- **publicKey**: string
  - RSA public key used for encrypting data.
  
**Responses example**
```json
{
  "id": "cbb00f18-88a0-4923-a421-8e28b17e988e",
  "publicKey": "MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQCOfJb/EYo9byGlMT2WEZbqI+whHbMZM8GM/ggIA+PIlahWJv5f+FhDjUhigJDIfmK/7UJEnjq35bBpKq1Y4yujHty76JzLJiV/Yl7+P8kLkNwITW+td73hkCwIs37aJl5vQPSuAGLD0bZmaf+YqZ78vrnux3UNs3j4rZxsyjyUMQIDAQAB"
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
