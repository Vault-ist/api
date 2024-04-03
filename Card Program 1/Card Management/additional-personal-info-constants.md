# Additional Personal Info Constants

`GET` **/v2/card/additional-personal-info/constants**

The endpoint is intended to fetch constants associated with additional personal information within the Card Program 1 functionality, enabling applications integrated with Card Program 1 to dynamically load and update lists of constants.

This ensures users have current information when entering their data or selecting options within the application.

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **additionalDocumentType**: array[string]
  - List of additional document types associated with personal information.
- **incomeSource**: array[string]
  - List of user income sources.
- **deprecatedIncomeSource**: array[string]
  - Deprecated list of income sources.
- **purposesOfAccountOpening**: array[string]
  - List of purposes for opening an account.
- **estimatedMonthlyTurnoverRange**: array[string]
  - List of estimated monthly turnover ranges.

  
**Responses example**
```json
  {
  "additionalDocumentType": [
    "Visa",
    "Residence permit",
    "Identification card",
    "Passport"
  ],
  "incomeSource": [
    "scholarship",
    "loans",
    "legacy",
    "salary",
    "dividends",
    "savings",
    "property_sale",
    "social_benefits",
    "individual_activities",
    "stocks_sale",
    "relatives",
    "winnings",
    "other"
  ],
  "deprecatedIncomeSource": [
    "company_sale",
    "divorce",
    "MLP",
    "drawings_income",
    "investment_income",
    "inheritance",
    "receivable_dividends",
    "private_property_sale",
    "retirement",
    "royalties_rewards",
    "capital_stocks_sale",
    "inheritance_gifts",
    "LOGW"
  ],
  "purposesOfAccountOpening": [
    "bs_companies",
    "bs_realestate",
    "investing",
    "salary",
    "savings"
  ],
  "estimatedMonthlyTurnoverRange": [
    "0-1000",
    "1001-3000",
    "3001-8000",
    "8001-15000",
    "15001-50000",
    "50001-99999"
  ]
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
