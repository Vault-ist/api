---
title: "Password Change Process"
slug: "password-change-process"
excerpt: "The password change process is designed to enhance the security of user accounts and allows users to periodically update their current password."
hidden: false
createdAt: "Tue Mar 19 2024 15:39:31 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 20 2024 16:44:36 GMT+0000 (Coordinated Universal Time)"
---
This process serves several key purposes:

- **Security Strengthening**: Regular password changes help prevent potential compromises of user accounts. If a password becomes known to malicious actors, changing the password provides an additional layer of protection.

- **Compliance with Security Standards**: Many security standards and regulations require periodic password changes to prevent unauthorized access and ensure compliance with security norms.

- **Protection Against Threats**: In the event of password leaks or other potential security threats, changing the password gives users the ability to react promptly and prevent unauthorized access to their account.

- **Account Security Support**: In cases where users suspect a compromise of their password or simply want to update their authentication credentials, the password change process provides a relevant mechanism for accomplishing this task.

### Step 1: Request for Password Change

The user  sends a password change request using the [PUT /v2/mobile/password/change](https://vault-bxou.readme.io/reference/change-password) endpoint. 

The request body includes data such as the current password (**currentPassword**) and the new password (**newPassword**).

![](https://files.readme.io/9d9e34a-image.png)

### Step 2: Server-Side Processing

The server processes the request and verifies the correctness of the current password. 

If the current password is correct, the server accepts the new password and updates it in the system.

### Step 3: Server Response

After a successful password change, the server returns a successful 200 OK status along with information about the operation result.

### Step 4: User Notification

Upon successful password change, the client may be notified that the password has been successfully updated.

As a result of these steps, the client successfully changes their current password to the new one provided in the request.

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
