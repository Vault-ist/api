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

<details>
<summary><span style="color: green;">200 - Success Response</span></summary>

The response status code indicates that the email has been successfully added.

- **Media type:** `application/json`

- **Body:** `application/json`

  - **result:** string
    - **Description:** Indicates the result of the email address confirmation operation.

</details>

<details>
<summary><span style="color: red;">400 - Error Response</span></summary>


The response status code indicates that the server cannot or will not process the request due to something perceived as a client error.

- **Media type:** `application/json`

- **Body:** `application/json`

  - **message:** string
    - **Description:** Message that will be displayed to the user.

  - **field:** string
    - **Description:** Specifies the field in the request that caused the error.

  - **errorId:** integer
    - **Description:** Integer identifier of the error.

  - **systemId:** string
    - **Description:** Identifier of the component.

  - **originalMessage:** string
    - **Description:** The original error message.

  - **errorStackTrace:** string
    - **Description:** The place where the error appeared in the code.

  - **data:** object
    - **Description:** Additional data related to the error, structured as key-value pairs.
      - **additionalProp1:** object
      - **additionalProp2:** object
      - **additionalProp3:** object
        
  - **error:** string
    - **Description:** Identifier of the error.

</details>


