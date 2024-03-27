---
title: "PayIn Process"
slug: "payin-process"
excerpt: "This comprehensive PayIn process covers card creation, billing address management, offer creation and update, as well as payment execution and status checking. It ensures a secure and transparent flow for users engaging in cryptocurrency transactions with fiat funds."
hidden: false
createdAt: "Tue Mar 19 2024 15:59:32 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 20 2024 16:44:45 GMT+0000 (Coordinated Universal Time)"
---
The goal of PayIn is to facilitate the purchase of cryptocurrency using fiat funds.

> ❗️ To perform the PayIn process, it is necessary to obtain the `KYC_0` using the [PUT Update Customer Profile](https://vault-bxou.readme.io/reference/update-customer-profile) endpoint.

### Step 1: Adding a new card and Billing Address

The user enters information for a new card, including card number, cardholder name, expiration date and billing address.

The system sends a [POST /v3/payin/card](https://vault-bxou.readme.io/reference/add-card) request to the server with information about the new card and billing address.

Upon successful addition, the server returns a 200 OK code, confirming that the card and billing address have been successfully added.

### Step 2: Retrieving Data for Offer Creation

To create an offer to purchase cryptocurrency, it's necessary to obtain the current exchange rate for the desired currency pair.

The system sends a request [GET /v3/payin/data](https://vault-bxou.readme.io/reference/get-available-rates-and-cards-payin) to the server to retrieve data about current exchange rates and other parameters, such as minimum and maximum amounts.

### Step 3: Creating an Offer without Immediate Fund Deduction

The user creates an offer for payment without an immediate fund deduction, specifying the amount, currency, and other parameters.

The system sends a [POST /v3/payin/offer](https://vault-bxou.readme.io/reference/create-offer-without-charging-customer) request to the server with information about the created offer.

The server returns information about the created offer, such as identifier, expiration date, exchange rate, and fees.

### Step 4: Updating an Existing Offer without Immediate Fund Deduction

The user updates parameters of an existing offer, such as amount, currency, or other details.

The system sends a request [PUT /v3/payin/offer/{offerId}](https://vault-bxou.readme.io/reference/update-existing-offer-without) to the server to update the offer.

Upon successful update, the server returns information about the offer.

### Step 5: Executing Offer Payment

The user makes a payment by providing details and other necessary information.

The system sends a request [POST /v3/payin/pay/{offerId}](https://vault-bxou.readme.io/reference/execute-offer-payment) to the server to execute the payment using the offer.

The server returns information about the transaction status, URL for redirecting the user, and other details.

### Step 6: Checking Payment Status

The system performs a request [GET /v3/payin/pay-callback](https://vault-bxou.readme.io/reference/pay-callback) to check the current payment status.

The server returns information about the payment status, amount, currency, card number, and other transaction details.

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
