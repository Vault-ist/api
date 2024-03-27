---
title: "SignIn Process"
slug: "signin-process"
excerpt: "The [SignIn](https://vault-bxou.readme.io/reference/signin) method is designed to authenticate users and grant them access to system resources."
hidden: false
createdAt: "Tue Mar 19 2024 13:42:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 20 2024 16:44:25 GMT+0000 (Coordinated Universal Time)"
---
This process typically involves the transmission of credentials, such as a phone number and password, from the client to the server. Upon successful authentication, the server issues temporary markers, such as access tokens, enabling the user to access secured resources without the need for reauthentication with each request.

> 💡 **SignIn Process**

1. The client initiates the sign-in process by sending a request with user credentials to the SignIn [POST /oauth/token](https://vault-bxou.readme.io/reference/signin) endpoint.

2. The server, upon receiving the request, verifies the provided credentials. In the case of successful authentication, the server generates two types of tokens:

   - `access_token`: This token serves as a key for the client to gain access to secured resources.

   - `refresh_token`: A special key that allows the client, whether it's an API or service, to obtain new access tokens without requiring the user to undergo a complete sign-in process.

3. The server provides these tokens to the client as part of the response to the sign-in request. The client then utilizes these tokens for subsequent requests to access secured resources.

This approach enhances security and user experience by allowing the client to maintain continuous access to protected resources without repeatedly going through the full authentication process.

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
