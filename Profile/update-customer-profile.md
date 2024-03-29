# Update customer profile

`PATCH` **/v2/customer/profile**

This endpoint is used to update the profile information of a customer.

## Request

### Body

**Media Type:** `application/json`

### Parameters

- **First Name**: string
  - A string representing the customer's first name.

- **Last Name**: string
  - A string representing the customer's last name.

- **Primary Currency**: string
  - A string representing the customer's primary currency.

- **Residence Country**: string
  - A string representing the customer's residence country.

- **Residence City**: string
  - A string representing the customer's residence city.

- **Residence Street**: string
  - A string representing the customer's residence street.

- **Residence Zip Code**: string
  - A string representing the customer's residence zip code.

- **Date of Birth**: string
  - A string representing the customer's date of birth.
  - Match pattern: `YYYY-MM-DDThh:mm:ss<TZDSuffix>`


### **Example body**
  
```json
{
  "lastName": "Schmidt",
  "firstName": "Anna",
  "dateOfBirth": "1990-05-20T00:00:00.000Z",
  "residenceCity": "Munich",
  "primaryCurrency": "EUR",
  "residenceStreet": "Examplestrasse",
  "residenceCountry": "DEU",
  "residenceZipCode": "12345"
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request PATCH \
  --url https://api.vault.sandbox.testessential.net/v2/customer/profile \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4' \
  --header 'Content-Type: application/json' \
  --data '{
  "lastName": "Schmidt",
  "firstName": "Anna",
  "dateOfBirth": "1990-05-20T00:00:00.000Z",
  "residenceCity": "Munich",
  "primaryCurrency": "EUR",
  "residenceStreet": "Examplestrasse",
  "residenceCountry": "DEU",
  "residenceZipCode": "12345"
}'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The server successfully processed the client's request and returned a positive result.
  

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
