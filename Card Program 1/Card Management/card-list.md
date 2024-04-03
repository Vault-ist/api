# Get Customer Cards for Program 1

`GET` **/v2/card/list**

This endpoint is designed to provide information about Card Program 1 cards for the customer.

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request GET \
  --url https://api.vault.sandbox.testessential.net/v2/card/list \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTIyMjQ1MTUsImlhdCI6MTcxMjEzODExNX0.8-moPaoJYz1kexcrOl2XIb3chF2Taf10IJeHEPnCOFI'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response includes details such as KYC status, a list of customer cards with their respective information, and the associated IBAN.
  
**Media type:** `application/json`

- **kycStatus**: object
  - Information about the status of the customer's identification process.
    - *status*: string
      - The current status.
    - *reason*: string
      - The reason for the current status (provided as a string).
- **cards**: array[object]
  - An array containing information about each card.
    - *id*: integer
      - Unique identifier of the card.
    - *expired*: string
      - The date and time when the card will expire.
    - *number*: string
      - Card number.
    - *balance*: object
      - Information about the card's balance.
        - *cardholderName*: string
          - Name of the cardholder.
        - *cardType*: string
          - Type of the card.
        - *status*: string
          - Card status.
        - *cardCompany*: string
          - The company that issued the card.
        - *monthlyIncome*: object
          - Monthly income of the cardholder. (Properties to be specified)
        - *monthlyExpenses*: object
          - Monthly expenses of the cardholder. (Properties to be specified)
    - *cardRequestId*: integer
      - Identifier of the card request.
    - *additionalStatuses*: array[string]
      - Additional statuses of the card.
    - *iban*: string
      - International Bank Account Number (IBAN) associated with the customer's wallet.

  
**Responses example**
```json
{
  "kycStatus": {
    "status": "PENDING",
    "reason": null
  },
  "cards": [
    {
      "cardType": "VIRTUAL",
      "status": "IN_PROGRESS",
      "cardCompany": "VISA",
      "cardRequestId": 8276,
      "additionalStatuses": [
        "ADDRESS",
        "TAXID",
        "PAID",
        "ADDITIONAL_PERSONAL_INFO",
        "KYC"
      ]
    }
  ],
  "iban": GB29NW5435345819
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
