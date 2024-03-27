---
title: "Password Reset Process"
slug: "password-reset-process"
excerpt: ""
hidden: false
createdAt: "Tue Mar 19 2024 14:17:09 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 20 2024 16:44:41 GMT+0000 (Coordinated Universal Time)"
---
Password reset is designed to enhance the security of user accounts by providing them the ability to change their current password in case they forget it or are unable to use the current password for some reason to log into the system.

### Step 1: Initiation of Password Change

The user sends a request to [POST /v2/mobile/password/reset](https://vault-bxou.readme.io/reference/resend-password).

Request headers include identification data: X-Merchant-ID, X-Fingerprint, X-Signature and the request body contains information about the mobile phone number.

![](https://files.readme.io/03726c1-image.png)

### Step 2: Receipt of SMS Confirmation Code

The system generates a confirmation code and sends an code to the specified phone number.  
For confirmation, the user enters the code via the [POST /v2/mobile/password/reset/confirm/code](https://vault-bxou.readme.io/reference/reset-confirm-code) endpoint.

If the initial confirmation code for the phone number was not received or has expired, the user can request a new code using the request to [POST /v2/mobile/password/reset](https://vault-bxou.readme.io/reference/resend-password).

![](https://files.readme.io/3af44d7-image.png)

### Step 3: Input of Confirmation Code and New Password

If the SMS confirmation code is valid, the user is prompted to enter and confirm the new password [POST v2/mobile/password/reset/confirm](https://vault-bxou.readme.io/reference/set-new-password).

> 📘 #### 💡The password must meet three conditions
> 
> - [x] The password must be at least 8 characters long.
> 
> - [x] The password must contain at least one digit.
> 
> - [x] The password must contain at least one letter.
> 
> - [ ] The password **must not** be equal to the phone number.
> 
> - [ ] The password **must not** contain information from the user profile.
> 
> - [ ] The password **cannot** be the same as any of the previous five passwords.
> 
> - [ ] The password **must not** be too simple, for example, "12345678".

![](https://files.readme.io/282f3c1-image.png)

### Step 4: Completion of the Process

The password is successfully reset.

Thus, the client initiates the password change process, verifies their identity using a code, and upon successful validation, updates the password.

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
