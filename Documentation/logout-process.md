---
title: "LogOut Process"
slug: "logout-process"
excerpt: ""
hidden: false
createdAt: "Tue Mar 19 2024 13:44:48 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 20 2024 16:44:30 GMT+0000 (Coordinated Universal Time)"
---
The [LogOut](https://vault-bxou.readme.io/reference/signout) method provides a mechanism for securely terminating a user session and invalidating temporary tokens issued during authentication. This process is crucial to prevent potential misuse and ensure the security of active user sessions.

> 💡 **Log Out Process**

1. The client initiates a request directed to the **SignOut** [POST /signout](https://vault-bxou.readme.io/reference/signout) endpoint. Automatically, the necessary tokens are provided:

   - `access_token`: This token serves as a key for the client to gain access to secured resources.

   - `refresh_token`: A special key that allows the client, whether it's an API or service, to obtain new access tokens without requiring the user to undergo a complete sign-in process.

2. Upon receiving the logout request, the server processes it, leading to the invalidation of the provided tokens and the deauthorization of the user.

3. Upon completion of the logout process, the client loses access to secured resources, and the user session concludes.

This mechanism ensures meticulous control over active sessions, mitigates against unauthorized access post-logout, and guarantees the secure termination of user sessions within the system.

To continue using the system, the client needs to perform [reauthorization](https://vault-bxou.readme.io/reference/signin).

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
