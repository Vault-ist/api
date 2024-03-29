# Feature Functionality Management

`GET` **/v2/catalog/operations**

This endpoint is designed to retrieve a simplified list of operations from the catalog. The catalog of operations may include various actions available for execution within the system.


## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`


- name: string  
  The name of the operation. All available operations in the Vault can be viewed here.

- constraint: string  
  Constraints or requirements associated with performing the operation. Possible values are:
  - `NONE`: Indicates that there are no specific constraints or requirements associated with the operation. The operation is allowed without any additional conditions.
  - `DISABLED`: Indicates that the operation is currently disabled or not allowed. Users attempting this operation may be restricted.
  - `MAINTENANCE`: Indicates that the operation is under maintenance, and it may not be available for execution during this period. Users are advised to wait until maintenance is complete.

- kycLevelPermissibleList: array of strings  
  KYC levels for which this operation is permissible.

- supportedVersion: string  
  The version of the supported operation.

**Soft Update:**

- **Description:** This type of update is only related to functional features and is not mandatory for all users.
- **When the check occurs:** The check occurs when accessing a specific function.
- **How the check is performed:** If the version of the feature on the client is less than the required one, using this feature becomes impossible.
- **Actions upon check:**
  - If the feature is isolated, a modal window appears with a proposal to update the application.
  - If the feature is not isolated (for example, screens with tabs for features), instead of the feature's starting screen, a screen appears with a message about the need to update.

  
**Responses example**
```json
 {
  "name": "PAYOUT_CRYPTO",
  "constraint": "NONE",
  "kycLevelPermissibleList": [
    "KYC_0"
  ],
  "currencyLimit": [
    "BCH",
    "OMG",
    "DAI",
    "CRPT",
    "DAO",
    "BTC",
    "MKR",
    "MAPS",
    "BAT",
    "ETH",
    "LTC",
    "USDC",
    "BUSD",
    "REP",
    "EVER",
    "QASH",
    "MATIC",
    "QLINDO",
    "CHO",
    "USDT",
    "DASH",
    "UNI",
    "GLEEC",
    "XRP",
    "LINK",
    "ZRX"
  ],
  "urlPatterns": [
    "/v1/wallet/send",
    "/v1/wallet/send/fee/*"
  ],
  "previewUrlPatterns": [
    "/v1/wallet/send/fee/\\b[a-zA-Z]+\\b"
  ],
  "supportedVersion": "1.0"
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
