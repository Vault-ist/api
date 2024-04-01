## Overview

The `KYC` (Know Your Customer) section comprises a set of endpoints designed for conducting customer identification procedures in accordance with established standards and regulations.

> 👍 **Vault offers distinct features categorized based on different KYC levels**

### PAYIN_CARD

For customers with `KYC_0` level, the **PAYIN_CARD** functionality enables processing payments via credit cards. This functionality includes the ability to obtain fiat exchange rates, data on available payment cards, add new cards, manage billing addresses, and create/update offers without charging the customer.

**Allowed Endpoints:**

- Get fiat rates: [GET /v3/payin/fiat-rates](https://vault-bxou.readme.io/reference/get-fiat-rates)
- Get available rates and cards data for pay in: [GET /v3/payin/data](https://vault-bxou.readme.io/reference/get-available-rates-and-cards-payin)
- Add new card: [POST /v3/payin/card](https://vault-bxou.readme.io/reference/add-card)
- Add card billing address: [POST /v3/payin/card/{cardId}/billing-address](https://vault-bxou.readme.io/reference/add-card-billing-address)
- Create an offer without charging customer: [POST /v3/payin/offer](https://vault-bxou.readme.io/reference/create-offer-without-charging-customer)
- Update existing offer without charging customer: [PUT /v3/payin/offer/{offerId}](https://vault-bxou.readme.io/reference/update-existing-offer-without)

For customers with `KYC_1` level, additional functionalities are available:  
**Allowed Endpoints:**

- Execute offer payment (do payment authorization) [POST /v3/payin/pay/{offerId}](https://vault-bxou.readme.io/reference/execute-offer-payment)
- Pay callback [GET /v3/payin/pay-callback](https://vault-bxou.readme.io/reference/pay-callback)

### PAYIN_CRYPTO

For customers with `KYC_0`, **PAYIN_CRYPTO** features are available, allowing them to make payments using cryptocurrencies. Specific endpoints are not mentioned, but users can seamlessly make cryptocurrency payments.

### PAYOUT_CARD

For customers with `KYC_0` level, the following **PAYOUT_CARD** functions are available:

- Get available rates and cards data for payout: [GET /v4/payout/data](https://vault-bxou.readme.io/reference/get-available-rates-and-cards-payout)
- Add a new card: [POST /v4/payout/card](https://vault-bxou.readme.io/reference/add-card-payout)
- Create a payout offer: [POST /v4/payout/offer](https://vault-bxou.readme.io/reference/create-payout-offer)
- Update a payout offer: [PUT /v4/payout/offer/{offerId}](https://vault-bxou.readme.io/reference/update-payout-offer)

For customers with `KYC_1` level, additional functionalities are available:

- Execute a payout offer [POST /v4/payout/pay/{offerId}](https://vault-bxou.readme.io/reference/execute-payout-offer)

### EXCHANGE

For customers with `KYC_0`, they can participate in currency exchange using the EXCHANGE features. The provided endpoints offer various operations related to mobile and online currency exchange.

**Allowed Endpoints:**

- Create an offer: [POST /v1/mobile/exchange/offer](https://vault-bxou.readme.io/reference/create-offer-exchange)
- Update an offer: [PUT /v1/mobile/exchange/offer](https://vault-bxou.readme.io/reference/update-offer-exchange)
- Execute an offer: [PUT /v1/mobile/exchange/offer/{offerId}](https://vault-bxou.readme.io/reference/execute-offer-exchange)
- Get available currencies for crypto exchanges: [GET /v2/exchange/currencies](https://vault-bxou.readme.io/reference/get-available-currencies-for-crypto-exchanges)

### CARD_PROGRAM_1_CARD

For customers with `KYC_0 Card Program 1` verification, the following actions are available:

- Get customer Card Program 1 Cards: [GET /v2/card/list](https://vault-bxou.readme.io/reference/card-list)
- Get prices for Card Program 1: [GET /v2/card/prices](https://vault-bxou.readme.io/reference/get-prices-for-card-program-1)

For customers with `KYC_1 Card Program 1` verification, additional actions are available.

- Activate virtual card [POST/v2/card/virtual/activate](https://vault-bxou.readme.io/reference/activate-virtual-card)
- Send customer soft block sms code [GET /v2/card/{cardId}/soft-block/code](https://vault-bxou.readme.io/reference/send-customer-soft-block-sms-code)
- Soft blocked Card Program 1 [POST/v2/card/{cardId}/soft-block](https://vault-bxou.readme.io/reference/soft-blocked-card-program-1)
- Send customer soft unblock sms code [GET /v2/card/{cardId}/soft-unblock/code](https://vault-bxou.readme.io/reference/send-customer-soft-block-sms-code)
- Customer soft unblock Card Program 1 [/v2/card/{cardId}/soft-unblock](https://vault-bxou.readme.io/reference/customer-soft-unblock-card-program-1)
- Request verification code for passcode [POST /v2/card/{id}/passcode/sms/send](https://vault-bxou.readme.io/reference/request-verification-code-for-passcode)
- Check verification code for passcode [POST /v2/card/{id}/passcode/sms/verify](https://vault-bxou.readme.io/reference/check-verification-code-for-passcode)
- Set passcode to Card Program 1 [POST /v2/card/{id}/passcode/code/set](https://vault-bxou.readme.io/reference/set-passcode-to-card-program-1)
- Get card number [POST /v2/card/{cardId}/number](https://vault-bxou.readme.io/reference/get-card-number)
- Get sms code to show card details [GET /v2/card/{cardId}/details/code](https://vault-bxou.readme.io/reference/get-sms-code-to-show-card-details)
- Get card details [POST /v2/card/{cardId}/details](https://vault-bxou.readme.io/reference/get-card-details)
- Get Card Price [GET /v2/card/card-requests/{id}/price/{currency}](https://vault-bxou.readme.io/reference/get-card-price)

### CARD_PROGRAM_1_PAYLOAD

For customers with `KYC_0 Card Program 1` verification, the following actions related to card payload management are available:

- Create new card request [POST /v2/card/card-requests](https://vault-bxou.readme.io/reference/create-new-card-request)
- Cancel card request [POST /v2/card/card-requests/{id}/cancel](https://vault-bxou.readme.io/reference/cancel-card-request)
- Update address for card request [PUT /v2/card/card-requests/{cardRequestId}/address](https://vault-bxou.readme.io/reference/update-address-for-card-request)
- Create order offer for Card Program 1 [POST /v2/card/card-requests/{cardRequestId}/address](https://vault-bxou.readme.io/reference/create-order-offer-for-card-program-1)

### CARD_PROGRAM_1_PAY_FOR_CARD

 For customers with`KYC_0 Card Program 1`verification, the following actions related to payment for cards are available:

- Pay card order offer [POST/v2/card/card-requests/payment-offer/{id}/confirm](https://vault-bxou.readme.io/reference/pay-card-order-offer)
- Confirm card payload offer [POST/v2/card/{cardId}/payload/offers/{offerId}/confirm](https://vault-bxou.readme.io/reference/confirm-card-payload-offer)

 For customers with`KYC_1 Card Program 1`verification, the following actions are available:

- Get limits, fees, and other data for card payload [GET /v2/card/{cardId}/payload/data](https://vault-bxou.readme.io/reference/get-limits-fees-and-other-data-for-card-payload)
- Update Card Payload Offer [PUT /v2/card/{cardId}/payload/offers/{offerId}](https://vault-bxou.readme.io/reference/update-card-payload-offer)
