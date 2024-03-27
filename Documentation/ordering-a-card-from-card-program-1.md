---
title: "Ordering a card from Card Program 1"
slug: "ordering-a-card-from-card-program-1"
excerpt: ""
hidden: false
createdAt: "Wed Mar 20 2024 07:57:05 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 20 2024 16:45:05 GMT+0000 (Coordinated Universal Time)"
---
### Step 1: Authentication

With the [POST /oauth/token](https://vault-bxou.readme.io/reference/signin) endpoint, the user logs into the application using their credentials, which include their `phone number` and `password`.

![](https://files.readme.io/6c0aafa-image.png)

### Step 2: Generate PIN code for application access

The user sets up a Personal Identification Number (PIN) that will be used to securely access the application.

![](https://files.readme.io/27adfd0-image.png)

### Step 3:  Open a new product

The user navigates to the section of the application where their existing wallets, cards, and card requests are displayed, using the endpoints [GET /v2/card/list](https://vault-bxou.readme.io/reference/card-list) and [GET /v2/wallets](https://vault-bxou.readme.io/reference/get-wallets).

To open a new product, the user needs to click the `+Open a new product` button.

![](https://files.readme.io/bc6b0d8-image.png)

### Step 4: Select crypto card

The user needs to select the `Crypto card` option.

![](https://files.readme.io/bdda397-image.png)

### Step 5: Choose card type

After completing the previous steps, the user will be presented with a window displaying information about the available types of cards, such as virtual. 

Additionally, the cost of the selected card will be indicated in this window. 

Once the user selects the desired card type, they will need to click the "Order the card" button. This action will initiate the card ordering process, which will be completed using the endpoint [POST /v2/card/card-requests](https://vault-bxou.readme.io/reference/create-new-card-request).

![](https://files.readme.io/5073fe5-image.png)

### Step 6: Accept Terms

The user reviews and agrees to the terms and conditions associated with ordering the card and using the service.

![](https://files.readme.io/c6a84f7-image.png)

### Step 7: Fill in Residence address

Using the endpoint [PUT /v2/card/card-requests/{cardRequestId}/address](https://vault-bxou.readme.io/reference/update-address-for-card-request), the user specifies their residential address where they want to receive the card.

![](https://files.readme.io/75d1df0-image.png)

### Step 8: Fill in Tax ID

With the [PUT /v1/customer/profile/tax](https://vault-bxou.readme.io/reference/update-customer-profile-tax-info) endpoint, the user enters their taxpayer identification number (TAX ID) for compliance with legal and tax regulations.

![](https://files.readme.io/794064f-image.png)

### Step 9: Provide Additional information

The user utilizes the endpoint [POST /v2/card/additional-personal-info](https://vault-bxou.readme.io/reference/additional-personal-info) to provide additional personal data or information required for card issuance or compliance with regulatory requirements.

![](https://files.readme.io/7690903-image.png)

### Step 10: Pass KYC in Ondato.

Using the endpoint [POST /v4/kyc/start](https://vault-bxou.readme.io/reference/start) with the platform parameter set to **WALLETTO**, the user undergoes the client verification (KYC) process through the Ondato platform. This process may involve providing a photo of an identity document for authenticity verification.

![](https://files.readme.io/5854949-image.png)

You can find instructions on how to integrate the Ondato SDK [here](https://vault-bxou.readme.io/docs/kyc-procedure).

### Step 11: Complete Selfie verification

The user takes a selfie to verify their identity, which is used as part of the KYC process.

![](https://files.readme.io/fa1fe20-image.png)

### Step 12: Submit documents to Ondato for verification

The uploaded documents and selfie are sent to Ondato for verification purposes.

![](https://files.readme.io/7d91371-image.png)

### Step 13: Successful verification by Ondato

Ondato verifies the provided documents and information, confirming the client's identity and their eligibility to receive the card. Upon successful verification, the endpoint [POST /v4/kyc/ondato/finished](https://vault-bxou.readme.io/reference/finish) returns a successful verification status.

![](https://files.readme.io/013c37f-image.png)

![](https://files.readme.io/96a7d06-image.png)

### Step 14: Await new status update for card order

The user awaits updates on the status of the card order.

![](https://files.readme.io/a1ddc37-image.png)

### Step 15: Card Ready for Activate

After that, the user needs to click the `Activate` button.

![](https://files.readme.io/c1e9f29-image.png)

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
