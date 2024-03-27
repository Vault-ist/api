---
title: "PayOut Process"
slug: "payout-process"
excerpt: "PayOut is a system designed for converting cryptocurrency into fiat currency and transferring it to a bank card."
hidden: false
createdAt: "Tue Mar 19 2024 16:14:02 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 20 2024 16:44:51 GMT+0000 (Coordinated Universal Time)"
---
The withdrawal process is organized through several steps, each represented by a specific API endpoint.

### Step 1: Adding a new card

The user initiates the PayOut process by sending a request to [POST /v4/payout/card](https://vault-bxou.readme.io/reference/add-card-payout) to add a new card.

The request body includes essential details such as the card number, cardholder's name, and expiration date.

The system processes the request and returns confirmation (200 OK) upon successful addition of the new card.

### Step 2: Retrieving available rates and card data

The user sends a request to [GET /v4/payout/data](https://vault-bxou.readme.io/reference/get-available-rates-and-cards-payout) to obtain information about available rates and cards.

The system returns information about user cards, currency pairs, exchange rates, and transaction fees.

### Step 3: Creating a payout offer

The user creates a payout offer by sending a request to [POST /v4/payout/offer](https://vault-bxou.readme.io/reference/create-payout-offer) with details such as the amount, source currency, target currency, and card ID.

The system returns detailed information about the created offer, including fees, exchange rates, and execution possibilities.

### Step 4: Updating a payout offer

If necessary, the user updates an existing payout offer by sending a request to [PUT /v4/payout/offer/{offerId}](https://vault-bxou.readme.io/reference/update-payout-offer) with changes, specifying the offerId.

The system returns detailed information about the updated offer, including modified fees, exchange rates, and execution possibilities.

### Step 5: Executing a payout offer

The user executes a payout offer by sending a request to [POST /v4/payout/pay/{offerId}](https://vault-bxou.readme.io/reference/execute-payout-offer) with the offer identifier, specifying offerId.

The system processes the payout transaction and returns the execution status.

The response provides details of the completed transaction, including deducted and received amounts, source and target currencies, as well as the transaction status.

[block:image]
{
  "images": [
    {
      "image": [
        "https://files.readme.io/0dcc41c-logo.png",
        "",
        "logo"
      ],
      "align": "right"
    }
  ]
}
[/block]
