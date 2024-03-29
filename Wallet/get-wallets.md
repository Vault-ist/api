# Get Wallets

`GET` **/v2/wallets**

This endpoint provides detailed information about user wallets, including associated accounts and fiat funds. It is designed for retrieving user wallet information.

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request GET \
  --url https://api.vault.sandbox.testessential.net/v2/wallets \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4'
```

## Responses

<details>
<summary><strong>200 - OK</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **wallets:** array[object]
  - List of created wallets with detailed information for each.
      
    - **id**: integer
      - Wallet identifier in Vault.
  
    - **name**: string
      - Name of the currency being created.
  
    - **externalId**: string
      - External identifier of the wallet in Vault.
  
    - **address**: string
      - Blockchain network address of a specific coin.
  
    - **currency**: string
      - Currency of the wallet. 
      - Example: `BTC, ETH, LTC etc.`
  
    - **baseCurrency**: string
      - Base currency of the wallet.
  
    - **pattern**: string
      - Wallet pattern.
  
    - **balance**: integer
      - Current balance of the wallet.
  
    - **limits**: object
      - Wallet limits.
    
        - **balanceString**: string
          - String representation of the balance.
    
        - **availableBalance**: integer
          - Balance that is currently available to the user.
  
    - **customerId**: integer
      - Identifier of the customer associated with the wallet.
  
    - **createdAt**: string<date-time>
      - Date and time of wallet creation. 
      - Match pattern: `YYYY-MM-DDThh:mm:ss<TZDSuffix>`
  
    - **isDebit**: boolean
      - Flag indicating whether the wallet is a debit wallet. 
      - **Default:** `true`
  
    - **allowOperations**: array[string]
      - Specifies the allowed operations with the wallet.
  
    - **color**: string
      - Color code associated with the wallet.
  
    - **fiat**: object
      - Information about the wallet in fiat currency.
    
        - **scale**: integer
          - A variable that specifies where the comma appears in a number.
    
        - **stub**: boolean
          - Indication of a stub or real wallet. 
          - **Default:** `true`
    
        - **walletCreationState**: string
          - The variable is intended to display the status of the wallet.
          - Allowed values:
            - `Ready`: Status means that a real address has been received and the wallet is ready for use.
            - `New`: Status means that the wallet has just been created.
            - `Getting`: Status means that the wallet is in the process of receiving a real address.
    
        - **iconUrl**: string
          - Link to wallet icon.
    
        - **network**: string
          - Wallet network.
  
    - **fiat**: object
      - Information about user fiat funds.
    
        - **customerCurrency**: string
          - Id, which is stored in the database.
    
        - **amount**: integer
          - A variable that indicates a specific value in customerCurrency.
    
        - **change**: integer
          - A variable that displays changes as a percentage (what happened to the wallet during the day).
    
        - **changePercent**: integer
          - Change percentage in fiat currency.
    
        - **rate**: integer
          - Exchange rate.

**Responses example**

```json
{
  "wallets": [
    {
      "id": -1,
      "fiat": {
        "rate": 0.12068,
        "amount": 0,
        "change": 0,
        "changePercent": -1.14,
        "customerCurrency": "EUR"
      },
      "name": "TRX",
      "stub": true,
      "color": "#EB322A",
      "debit": true,
      "scale": 5,
      "limits": {
        "PAYOUT_CRYPTO": {
          "all": 0,
          "min": 0.00001
        }
      },
      "address": "",
      "balance": 0,
      "currency": "TRX",
      "customerId": 5787,
      "balanceString": "0",
      "allowOperations": [],
      "availableBalance": 0,
      "walletCreationState": "READY"
    },
    {
      "id": 5822,
      "fiat": {
        "rate": 0.63421,
        "amount": 0,
        "change": 0,
        "changePercent": 10.87,
        "customerCurrency": "EUR"
      },
      "name": "XRP",
      "stub": false,
      "color": "#262A3C",
      "debit": true,
      "scale": 6,
      "limits": {
        "PAYOUT_CRYPTO": {
          "all": 0,
          "min": 20
        }
      },
      "address": "rnrve1cZDyLv225wv9Xre1nD5EWRjS4CW2?dt=27",
      "balance": 0,
      "pattern": "^r[0-9a-zA-Z]{24,34}(\\?dt=\\d+)?$",
      "currency": "XRP",
      "customerId": 5787,
      "balanceString": "0",
      "allowOperations": [
        "TRANSFER_MOBILE",
        "PAYIN_CRYPTO",
        "WALLETTO_CARD_PAYLOAD",
        "WALLETTO_CARD",
        "COMMON",
        "WALLET_SCREEN",
        "PAYOUT_CRYPTO",
        "EXCHANGE",
        "PAYIN_CARD",
        "PAYOUT_CARD",
        "WALLETTO_PAY_FOR_CARD",
        "Common"
      ],
      "availableBalance": 0,
      "walletCreationState": "READY"
    },
    {
      "id": 5792,
      "fiat": {
        "rate": 65628.5,
        "amount": 130540.48,
        "change": 659.74,
        "changePercent": 0.51,
        "customerCurrency": "EUR"
      },
      "name": "BTC",
      "stub": false,
      "color": "#FF8724",
      "debit": true,
      "scale": 8,
      "limits": {
        "PAYOUT_CRYPTO": {
          "all": 1.98655697,
          "min": 0.001
        }
      },
      "address": "2NFnhQrRUbQT57YSx9oZRwWZrTXu8PVFQzq",
      "balance": 1.98908205,
      "pattern": "^(bitcoin:|btc:)?([123][a-km-zA-HJ-NP-Z1-9]{25,34}$)|(bc1[\\w]{25,}$)",
      "currency": "BTC",
      "customerId": 5787,
      "balanceString": "1.98908205",
      "allowOperations": [
        "TRANSFER_MOBILE",
        "PAYIN_CRYPTO",
        "WALLETTO_CARD_PAYLOAD",
        "WALLETTO_CARD",
        "COMMON",
        "WALLET_SCREEN",
        "PAYOUT_CRYPTO",
        "EXCHANGE",
        "PAYIN_CARD",
        "PAYOUT_CARD",
        "WALLETTO_PAY_FOR_CARD",
        "Common"
      ],
      "availableBalance": 1.98908205,
      "walletCreationState": "READY"
    },
    {
      "id": 5794,
      "fiat": {
        "rate": 89.09,
        "amount": 356.28,
        "change": 17.48,
        "changePercent": 4.91,
        "customerCurrency": "EUR"
      },
      "name": "LTC",
      "stub": false,
      "color": "#9B9AA9",
      "debit": true,
      "scale": 8,
      "limits": {
        "PAYOUT_CRYPTO": {
          "all": 3.993721,
          "min": 0.01
        }
      },
      "address": "QbRntihVRPxio1epdKaHpG2d1y8zKokkVm",
      "balance": 3.999,
      "pattern": "^(litecoin:)?([LM3Q2][a-km-zA-HJ-NP-Z1-9]{26,33})|(ltc1[\\w]{25,})$",
      "currency": "LTC",
      "customerId": 5787,
      "balanceString": "3.999",
      "allowOperations": [
        "TRANSFER_MOBILE",
        "PAYIN_CRYPTO",
        "WALLETTO_CARD_PAYLOAD",
        "WALLETTO_CARD",
        "COMMON",
        "WALLET_SCREEN",
        "PAYOUT_CRYPTO",
        "EXCHANGE",
        "PAYIN_CARD",
        "PAYOUT_CARD",
        "WALLETTO_PAY_FOR_CARD",
        "Common"
      ],
      "availableBalance": 3.999,
      "walletCreationState": "READY"
    }
  ]
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
