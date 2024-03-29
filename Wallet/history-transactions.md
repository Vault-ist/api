# History Transactions

`GET` **/v2/history/operations**

This endpoint is designed to retrieve the user's wallet transaction history, providing information about various operations, including currency exchange, cryptocurrency receipt, funding from various sources, card withdrawal, transfer to another wallet, and mobile transfers.


## Request

### Query Parameters

- **currencyFilter**: array
  - Filter based on currencies.

- **offset**: integer<int64>
  - Offset limit for pagination.
  - **Default:** `0`

- **size**: integer<int64>
  - Number of transactions in the results.
  - **Default:** `50`

- **typeFilter**: array or string
  - Indicates the type of operations to filter. Refer to the [Types of Filters](https://github.com/crypterium-com/api-vault.wiki.git) section for details on all types of transaction history filters.
  - **Allowed values:**
    - `UNKNOWN`
    - `RECEIVE_CRYPTO`
    - `PAYIN_CARD`
    - `PAYIN_ADVCASH`
    - `PAYOUT_CARD`
    - `EXCHANGE`
    - `SEND_TO_PHONE`
    - `SEND_TO_WALLET`

```json json_schema
{
  "X-Merchant-ID": {
    "type": "string",
    "required": true,
    "description": "Identification of requests from users of a specific partner.",
    "default": "bece038f-2e46-49f4-b25e-89cd38d6dc16"
  }
}
```

#### **Request Sample: cURL**

At the time of sending the request, the curl command should be as follows:

```curl cURL
curl --request GET \
  --url 'https://api.vault.sandbox.testessential.net/v2/history/operations?typeFilter=UNKNOWN&offset=0&size=50' \
  --header 'Accept: application/json' \
  --header 'Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIwNTFhYTc3Mi0yNDk4LTQ0ZTEtODdmYi0zYzNhZDdlMTY1ODgiLCJleHAiOjE3MTE3ODM4OTYsImlhdCI6MTcxMTY5NzQ5Nn0.GBWhOHEIbiOipMa1kXMsamNqT1I6pFBe3-gZ3me1bM4'
```

## Responses

<details>
<summary><strong>200 - Success Response</strong></summary>
  
The response status code indicates that the request was successfully processed.
  
**Media type:** `application/json`
  
- **Data Format:** Array of objects

    Each object contains the following information:

    - **sendToPhoneModel:**
      - Model for sending to a phone operation.
        - **amount:** Array of objects
          - **operationId:** string
            - A unique identifier for the operation.
          - **operationDate:** string<date-time>
            - The date and time when the operation occurred.
            - Match pattern: `YYYY-MM-DDThh:mm:ss<TZDSuffix>`
          - **operationStatus:** string
            - Status of the operation.
          - **exchangeModel:** object
            - Details about an exchange operation.
              - **fromAddress:** string
                - Sender's address in the exchange operation.
              - **toAddress:** string
                - Recipient's address in the exchange operation.
              - **debitAmount:** object
                - Value and currency of the debited amount.
              - **creditAmount:** object
                - Amount credited in the exchange.
              - **exchangeRate:** object
                - Exchange rate details.
          - **receiveCryptoModel:** object
            - Details about receiving cryptocurrency.
              - **toAddress:** string
                - Receiver's address.
              - **fromAddress:** string
                - Sender's address.
              - **amount:** object
                - Amount with currency information.
              - **txHash:** string
                - Transaction hash for the received crypto.
          - **payinAdvcashModel:** object
            - Details about a Payin operation using Advcash.
              - **email:** string
                - Email associated with the Advcash payment.
              - **toAddress:** string
                - Destination address for Advcash payment.
              - **debitAmount:** object
                - Debit amount details for Advcash payment.
              - **creditAmount:** object
                - Credit amount details for Advcash payment.
              - **feeAmount:** object
                - Fee amount details for Advcash payment.
              - **exchangeRate:** object
                - Exchange rate details for Advcash payment.
          - **payinCardModel:** object
            - Details about a Payin operation using a card.
              - **fromCardPAN:** string
                - Source card's PAN for card payment.
              - **toAddress:** string
                - Destination address for card payment.
              - **debitAmount:** object
                - Debit amount details for card payment.
              - **creditAmount:** object
                - Credit amount details for card payment.
              - **feeAmount:** object
                - Fee amount details for card payment.
              - **exchangeRate:** object
                - Exchange rate details for card payment.
          - **payoutCardModel:** object
            - Details about a Payout operation to a card.
              - **fromAddress:** string
                - Source address for card payout.
              - **toCardPAN:** string
                - Destination card's PAN for card payout.
              - **debitAmount:** object
                - Debit amount details for card payout.
              - **creditAmount:** object
                - Credit amount details for card payout.
              - **feeAmount:** object
                - Fee amount details for card payout.
              - **exchangeRate:** object
                - Exchange rate details for card payout.
          - **sendToWalletModel:** object
            - Model for sending to another wallet operation.
              - **fromAddress:** string
                - Source address for the send operation.
              - **toAddress:** string
                - Destination address for the send operation.
              - **debitAmount:** object
                - Amount debited in the send operation.
              - **creditAmount:** object
                - Amount credited in the send operation.
              - **feeAmount:** object
                - Fee amount details.
              - **txHash:** string
                - Transaction hash for the send operation.
          - **sendToPhoneModel:** object
            - Model for sending to a phone operation.
              - **fromAddress:** string
                - Source address for the send operation.
              - **toPhone:** string
                - Destination phone number for the send operation.
              - **amount:** object
                - Amount details for the send operation.

   **Responses example**
```json
{
  "operationId": "5143535135",
  "exchangeModel": null,
  "operationDate": "2023-11-17T11:45:19.878Z",
  "payinCardModel": {
    "feeAmount": {
      "value": 0,
      "currency": "EUR"
    },
    "toAddress": "0x5fa3b9328c1512414fefw124391e1589b09",
    "debitAmount": {
      "value": 54.80299577,
      "currency": "USDT"
    },
    "fromCardPAN": "345345****3442",
    "creditAmount": {
      "value": 51,
      "currency": "EUR"
    },
    "exchangeRate": {
      "rate": 1.0745685444480626,
      "multiplier": 1,
      "sourceCurrency": "EUR",
      "targetCurrency": "USDT"
    }
  },
  "operationStatus": "FAILED",
  "payoutCardModel": null,
  "sendToPhoneModel": null,
  "payinAdvcashModel": null,
  "sendToWalletModel": null,
  "receiveCryptoModel": null
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
