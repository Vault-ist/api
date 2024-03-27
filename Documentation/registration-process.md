# Registration Process

### Step 1: Phone Number Registration

The user initiates registration by sending a request to [POST /v2/mobile/signup](https://vault-bxou.readme.io/reference/create-account), specifying the phone number and password in the request body.

> 🚧 When re-registering in the system, it is necessary to use a new phone number that has not been used before.

***

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

![](https://files.readme.io/bf43d86-image.png)

### Step 2: Phone Number Confirmation

A SMS code is sent to the provided phone number for confirmation. The user confirms the phone number by submitting the verification code through the [POST /v2/mobile/phone/confirm](https://vault-bxou.readme.io/reference/confirm-phone-number) endpoint.

![](https://files.readme.io/9e98270-image.png)

If the initial confirmation code is not received or its validity expires, the user can request a resend using the [POST /v2/mobile/phone/verify/resend ](https://vault-bxou.readme.io/reference/resend-code) endpoint.

Upon successful confirmation, the system issues access tokens (`access_token` and `refresh_token`), allowing the user to authenticate.

- `access_token`: This token serves as a key for the client to gain access to secured resources.
- `refresh_token`: A special key that allows the client, whether it's an API or service, to obtain new access tokens without requiring the user to undergo a complete sign-in process.

### Step 3: Account Creation

The system creates a user account, providing a unique userId.

### Step 4: Adding Email Address

The user needs to add an email address to the account by sending a request to the [PUT /v2/mobile/email/add](https://vault-bxou.readme.io/reference/add-email) endpoint.

![](https://files.readme.io/458a309-image.png)

Upon successful completion of the request with a 200 (OK) response code, the system automatically triggers the sending of a confirmation email. The email will be sent immediately after the request is successfully processed.

### Step 5: Email Address Confirmation

The endpoint [POST /v2/mobile/email/verify/resend](https://vault-bxou.readme.io/reference/resend-email) is used to send an email to the specified email address. The user confirms the email address by clicking a button in the received email, which triggers a call to the endpoint[GET /v2/mobile/email/confirm](https://vault-bxou.readme.io/reference/confirm-email). After successful email address confirmation, the user receives a new verification identifier.

> 📘 In the user profile, to resend the confirmation email to the specified email address, you can use the following endpoint: [POST /v2/mobile/email/verify/resend](https://vault-bxou.readme.io/reference/resend-email). This endpoint allows you to resend the verification notification if the user did not receive it initially.

Indeed, the registration process encompasses the creation of an account based on a phone number, the confirmation of that number, and the addition as well as the confirmation of an email address. All these steps are geared towards ensuring security and verifying the user's identity throughout the process.  

<img src="https://files.readme.io/0dcc41c-logo.png" alt="Логотип" style="float: right; margin-left: 30px;">



