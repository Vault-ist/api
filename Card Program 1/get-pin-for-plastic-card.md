---
title: "Get PIN for Plastic Card"
slug: "get-pin-for-plastic-card"
excerpt: "This endpoint is designed for retrieving the PIN code for a specific plastic card."
hidden: true
createdAt: "Mon Mar 18 2024 12:19:44 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 20 2024 15:59:45 GMT+0000 (Coordinated Universal Time)"
---
This endpoint is intended for securely obtaining the PIN code for a banking card. The user must provide the necessary data for authentication and encryption, after which the system returns the corresponding PIN code.

The variable `publicKey` can be obtained using the endpoint [GET /v2/card/rsa-public-key](https://vault-bxou.readme.io/reference/get-rsa-key).
