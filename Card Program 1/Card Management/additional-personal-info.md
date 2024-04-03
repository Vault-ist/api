# Additional Personal Info

`POST` **/v2/card/additional-personal-info**

The endpoint is intended for submitting additional personal information within the Card Program 1.

## Request

**Media Type:** `application/json`

### Headers

- *User-Agent*: string
  - User identifier making the request.
  - **Default:** `vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24`

### Body

- **dataCorrectnessConfirmation**: boolean
  - Confirmation of the correctness of the submitted data.
  - **Default:** `true`
- **additionalDocumentType**: string
  - Type of additional document associated with personal information.
- **additionalDocumentNumber**: string
  - Number of the additional document.
- **additionalDocumentExpireDate**: string<date-time>
  - Expiry date of the additional document in ISO 8601 format.
  - **Match pattern:** `YYYY-MM-DDThh:mm:ss<TZDSuffix>`
- **additionalDocumentCountry**: string
  - Country associated with the additional document.
- **additionalDocumentComment**: string
  - Additional comments or information related to the document.
- **isPepRelated**: boolean
  - Indicates whether the person is politically exposed.
  - **Default:** `true`
- **pepRelatedPerson**: string
  - Information related to politically exposed persons.
- **isUsRelated**: boolean
  - Indicates whether the person is related to the United States.
  - **Default:** `true`
- **usRelatedPerson**: string
  - Information related to persons with a connection to the United States.
- **incomeSource**: array[string]
  - List of user income sources.
- **additionalIncomeSource**: string
  - Additional information about the income source.
- **estimatedMonthlyTurnoverRange**: string
  - Estimated monthly turnover range.


### **Example body**
  
```json
{
  "additionalDocumentType": "string",
  "additionalDocumentNumber": "string",
  "additionalDocumentExpireDate": "2019-08-24T14:15:22Z",
  "additionalDocumentCountry": "string",
  "additionalDocumentComment": "string",
  "isPepRelated": true,
  "pepRelatedPerson": "string",
  "isUsRelated": true,
  "usRelatedPerson": "string",
  "incomeSource": [
    "string"
  ],
  "additionalIncomeSource": "string",
  "estimatedMonthlyTurnoverRange": "string",
  "dataCorrectnessConfirmation": true
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request POST \
  --url https://api.vault.sandbox.testessential.net/v2/card/additional-personal-info \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiI0ZGQyYzA2YS01ZTAyLTQ3ZjMtYWM5Zi1hYzE4Y2Q5Y2ZiNDQiLCJleHAiOjE3MTIyMzAyOTIsImlhdCI6MTcxMjE0Mzg5Mn0.Zf1C96fU6YXbxLec3BSjhqZPRpSRLU-rkj5aw2TL7wY' \
  --header 'Content-Type: application/json' \
  --header 'User-Agent: vault/4.0(508) dart/3.2 (dart:io) ios/17.3.1; iphone 9da12fa6-716c-4cdc-a24' \
  --data '{
  "additionalDocumentType": "string",
  "additionalDocumentNumber": "string",
  "additionalDocumentExpireDate": "2019-08-24T14:15:22Z",
  "additionalDocumentCountry": "string",
  "additionalDocumentComment": "string",
  "isPepRelated": true,
  "pepRelatedPerson": "string",
  "isUsRelated": true,
  "usRelatedPerson": "string",
  "incomeSource": [
    "string"
  ],
  "additionalIncomeSource": "string",
  "estimatedMonthlyTurnoverRange": "string",
  "dataCorrectnessConfirmation": true
}'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`

- **result**: string
  - A string indicating the result of the submission of additional personal information.


  
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
