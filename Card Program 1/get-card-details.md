---
title: "Get Card Details"
slug: "get-card-details"
excerpt: "This endpoint is designed for retrieving detailed information about a specific card."
hidden: false
createdAt: "Tue Mar 19 2024 06:54:03 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Tue Mar 19 2024 06:54:03 GMT+0000 (Coordinated Universal Time)"
---
This endpoint is intended for securely obtaining detailed information about the specified card, including the card number, CVV, expiry date, and cardholder name. The verification code and public key are used for authentication and encryption, respectively, to enhance security during the retrieval process.

The variable `publicKey` can be obtained using the endpoint [GET /v2/card/rsa-public-key](Api/Card-Program-1.yaml/paths/~1v2~1card~1rsa-public-key/get).
