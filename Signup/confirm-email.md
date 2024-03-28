# Confirm Email

 <span style="color: green;">`GET`</span> **/v2/mobile/email/confirm**

The endpoint is to confirm an email address.

> 🚧 The data must be encoded in **base64** format using your frontend

## Query Parameters

- **email**: string *(required)*
  - Description: The email address to be confirmed.

- **event**: string *(required)*
  - Description: The event related to the email confirmation.

- **token**: string *(required)*
  - Description: The token associated with the email confirmation process. It is sent to the user via email as part of the confirmation process.

## Responses

<details>
<summary><span style="color: green;">200 - OK</span></summary>

The response status code indicates that the request was successfully processed.

**Media type:** `application/json`

- **result:** string
  - Provides information about the outcome of the registration operation.

**Responses example**
```json
{
  "result": "ok"
}
```
</details>

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


