# Feature Functionality Management

`GET` **/v2/customer/profile**

The endpoint is designed to retrieve the current customer profile. This request returns information about the customer, including their identification details, contact information, consent statuses, Know Your Customer (KYC) level, loyalty level, balance, additional account parameters, and other relevant details.

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  
If a user's field with information is not filled (meaning it has a NULL value), then in the response to a GET request to the /v2/customer/profile endpoint, the value of this field will not be included in the response body.
  
**Media type:** `application/json`


- **email**: string
  - Customer's email address.
  
- **confirmedEmail**: boolean
  - Confirmation status of the email.
  - **Default**: `true`
  
- **phone**: string
  - Customer's phone number.
  
- **firstName**: string
  - Customer's first name.
  
- **lastName**: string
  - Customer's last name.
  
- **primaryCurrency**: string
  - Main currency.
  
- **residenceCountry**: string
  - Country of residence for the customer.
  
- **residenceState**: string
  - Customer's residence state.
  
- **residenceCity**: string
  - Customer's residence city.
  
- **residenceStreet**: string
  - Customer's residence street.
  
- **residenceZipCode**: string
  - Customer's residence postal code.
  
- **pushEnabled**: boolean
  - Whether push notifications are enabled.
  - **Default**: `true`
  
- **enabled2FA**: boolean
  - Whether two-factor authentication is enabled.
  - **Default**: `true`
  
- **dateOfBirth**: string<date-time>
  - Date of birth for the customer.
  - **Match pattern**: `YYYY-MM-DDThh:mm:ss<TZDSuffix>`
  
- **veroId**: string
  - Customer's identifier in the Vero system.

  
**Responses example**
```json
 {
  "email": "test@gmail.com",
  "confirmedEmail": false,
  "phone": "447871236669",
  "firstName": "Anna",
  "lastName": "Schmidt",
  "primaryCurrency": "EUR",
  "residenceCountry": "DE",
  "residenceCity": "Munich",
  "residenceStreet": "Examplestrasse",
  "residenceZipCode": "12345",
  "pushEnabled": true,
  "enabled2FA": false,
  "dateOfBirth": "1990-05-20T00:00:00",
  "veroId": "423db895-a10d-4114-a457-ad9291ea34cb"
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
