The `Send` section is intended for performing operations related to sending coins from one wallet to another. 

This section provides several endpoints that enable the following actions:

- **Sending coins to another wallet:** This process is performed using the [`/v1/wallet/send`](https://github.com/crypterium-com/api-vault/blob/main/Send/send-coins.md) endpoint. When calling this endpoint, information about the recipient's address, the amount to be transferred, the currency, and, if necessary, the transaction fee is provided. Upon successful submission of the request, the response includes transaction information, including the transaction ID and confirmation of the send.

- **Validating a request to send coins:** This process is carried out using the [`/v1/wallet/send/validate`](https://github.com/crypterium-com/api-vault/blob/main/Send/validate-send-coins.md?plain=1) endpoint. Before executing the transaction, a preliminary check of the send request can be performed to ensure that all data for sending coins is correctly specified. This allows verifying that the transaction can be successfully executed.

- **Getting information about the transaction fee:** This process is performed using the [`/v1/wallet/send/fee/{currency}`](https://github.com/crypterium-com/api-vault/blob/main/Send/get-fee.md) endpoint. When calling this endpoint, information about the currency for which the fee is required is provided. The response includes information about the fee amount, currency, and transaction type.

Indeed, the `Send` section provides a convenient way to transfer coins between wallets, as well as the ability to validate a request and obtain information about the transaction fee.
