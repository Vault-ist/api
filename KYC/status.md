# Status

`GET` **/v2/customer/kyc/data**

The endpoint is intended to retrieve Know Your Customer (KYC) data for a customer. KYC is the process of verifying a customer's identity in accordance with established standards and regulations.

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
A successful request to obtain customer data within the KYC (Know Your Customer) process.
  
**Media type:** `application/json`

### Body

- **kycLevel** (string): Indicates the current KYC level of the customer.
  - *Example:* `NONE`, `KYC1`, `KYC2`, `KYC3`

- **kyc1ClientData** (object): KYC Level 1 data for the customer.
  - **status** (string): Status of KYC Level 1.
    - *Allowed values:*
      - `APPROVED`: This status indicates that the verification has been successfully completed, and all client data meets the established requirements.
      - `UNDEFINED`: This status indicates that the client's status is not defined or is unknown for some reason. It could be a temporary state when the information has not yet been received or is being processed.
      - `UNDER_REVIEW`: This status indicates that the data has been submitted for verification, but the process is not yet completed. This could be related to the need for additional verification or confirmation of data.
      - `DENIED`: This status indicates client rejection. It means that the client's data does not meet the requirements or has been rejected for some other reason.
  - **reason** (string): Reason for rejection if the status is DENIED. This is an internal rejection code.
  - **rejectFormattedMessage** (string): Message explaining the reason for rejection, intended for display on the frontend.

- **kyc2ClientData** (object): KYC Level 2 data for the customer.
  - **status** (string): Status of KYC Level 2.
    - *Allowed values:*
      - `APPROVED`: This status indicates that the verification has been successfully completed, and all client data meets the established requirements.
      - `UNDEFINED`: This status indicates that the client's status is not defined or is unknown for some reason. It could be a temporary state when the information has not yet been received or is being processed.
      - `UNDER_REVIEW`: This status indicates that the data has been submitted for verification, but the process is not yet completed. This could be related to the need for additional verification or confirmation of data.
      - `DENIED`: This status indicates client rejection. It means that the client's data does not meet the requirements or has been rejected for some other reason.
  - **reason** (string): Reason for rejection if the status is DENIED. This is an internal rejection code.
  - **rejectFormattedMessage** (string): Message explaining the reason for rejection, intended for display on the frontend.

- **kyc3ClientData** (object): KYC Level 3 data for the customer.
  - **status** (string): Status of KYC Level 3.
    - *Allowed values:*
      - `APPROVED`: This status indicates that the verification has been successfully completed, and all client data meets the established requirements.
      - `UNDEFINED`: This status indicates that the client's status is not defined or is unknown for some reason. It could be a temporary state when the information has not yet been received or is being processed.
      - `UNDER_REVIEW`: This status indicates that the data has been submitted for verification, but the process is not yet completed. This could be related to the need for additional verification or confirmation of data.
      - `DENIED`: This status indicates client rejection. It means that the client's data does not meet the requirements or has been rejected for some other reason.
  - **reason** (string): Reason for rejection if the status is DENIED. This is an internal rejection code.
  - **rejectFormattedMessage** (string): Message explaining the reason for rejection, intended for display on the frontend.

- **daysToExpireKyc** (integer): Specifies the number of days until KYC1 expires. This is applicable only to KYC1.

- **remainingAmount** (object): Information about the remaining funds in the client's account.
  - **value** (integer): The value of the remaining amount.
  - **currency** (string): The currency of the amount.

- **blockedAmount** (object): Information about the funds blocked in the client's account.
  - **value** (integer): Value of the blocked amount.
  - **currency** (string): Currency of the blocked amount.

  
**Responses example**
```json
{
  "kycLevel": "KYC_1",
  "blockedAmount": {
    "value": 0,
    "currency": "EUR"
  },
  "kyc1ClientData": {
    "reason": null,
    "status": "APPROVED",
    "rejectFormattedMessage": null
  },
  "kyc2ClientData": {
    "reason": null,
    "status": "UNDEFINED",
    "rejectFormattedMessage": null
  },
  "kyc3ClientData": {
    "reason": null,
    "status": "UNDEFINED",
    "rejectFormattedMessage": null
  },
  "daysToExpireKyc": 1207,
  "remainingAmount": {
    "value": 9599.18,
    "currency": "EUR"
  }
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
