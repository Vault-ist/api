# Update Customer Profile Tax Info

`PUT` **/v1/customer/profile/tax**

This endpoint is used to update the tax information in the customer's profile. The customer provides their tax identification number `taxId` and the associated country `taxCountry`.


## Request

**Media Type:** `application/json`

### Parameters

- **taxId**: *string* *(required)*
  - Customer's tax identification number.

- **taxCountry**: *string* *(required)*
  - Country associated with the customer's tax information.

### **Example body**
  
```json
{
  "taxId": "12345678910",
  "taxCountry": "DEU"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request PUT \
  --url https://api.vault.sandbox.testessential.net/v1/customer/profile/tax \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiJlOTBmNTNiOC05MTc0LTQyZWUtYTVjNS04ZTA0ZGM2MzA5NWYiLCJleHAiOjE3MTIyMzY0MTAsImlhdCI6MTcxMjE1MDAxMH0.1jyJQ7npbGowVG_AbY3iWQwRv8XepgLx7u2UVyVtMgk' \
  --header 'Content-Type: application/json' \
  --data '{
  "taxId": "12345678910",
  "taxCountry": "DEU"
}'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
**Responses example**
```json
{
  "customerId": 189,
  "email": "test@gmail.com",
  "confirmedEmail": false,
  "phone": "447871232323",
  "firstName": "Anna",
  "lastName": "Schmidt",
  "primaryCurrency": "EUR",
  "country": "LT",
  "residenceCountry": "DEU",
  "residenceCity": "Munich",
  "residenceStreet": "Examplestrasse",
  "residenceZipCode": "12345",
  "completedKycLevel": "NONE",
  "completedKycLevelList": [
    "KYC_0"
  ],
  "loyaltyLevel": "Bronze",
  "wasInvited": false,
  "payoutVersion": 1,
  "pushEnabled": true,
  "acceptedGramTermsAndConditions": false,
  "enabled2FA": false,
  "payinIsBlocked": false,
  "locale": "en",
  "badgeNames": [],
  "taxId": "12345678910",
  "taxCountry": "DEU",
  "taxIdValid": true,
  "dateOfBirth": "1990-05-20T00:00:00.000Z",
  "transaction2FaMethod": "EMAIL",
  "activePushDevicesExists": false,
  "acceptChoiseTerms": true,
  "acceptInsuranceTerms": false,
  "acceptDualCurrencyTerms": false,
  "veroId": "e936de5c-a5a6-45f2-9a80-6f919b6e6eb8",
  "isTemporaryPassword": false
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
