---
title: "History Transactions"
slug: "history-transactions"
excerpt: "This endpoint is designed to retrieve the user's wallet transaction history, providing information about various operations, including currency exchange, cryptocurrency receipt, funding from various sources, card withdrawal, transfer to another wallet, and mobile transfers."
hidden: false
createdAt: "Thu Mar 14 2024 08:35:36 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 20 2024 12:43:33 GMT+0000 (Coordinated Universal Time)"
---
# Types of Filters

For transaction stories, the following types of filters can be configured:

- `UNKNOWN` - Indicates no specific filter is applied, retrieving all operations.
- `RECEIVE_CRYPTO` - Refers to external transfer operations, involving the receipt of cryptocurrency from external sources.
- `PAYIN_CARD` - Denotes operations related to purchasing cryptocurrency using a linked bank card.
- `PAYIN_ADVCASH` - Represents operations involving the purchase of cryptocurrency through the `ADVCASH` service.
- `PAYOUT_CARD` - Indicates fiat withdrawal operations to a linked card.
- `EXCHANGE` - Refers to regular cryptocurrency exchange transactions.
- `SEND_TO_PHONE` - Denotes cryptocurrency transfer operations initiated by providing the recipient's phone number.
- `SEND_TO_WALLET` - Represents cryptocurrency transfer operations initiated by providing the recipient's wallet address.
