---
#Sandbox

## Step 1: Authorization in the Sandbox

To utilize the sandbox, navigate to the following link:

<https://api.vault.sandbox.testessential.net/swagger-ui/index.html?urls.primaryName=White%20label#/>

It is essential to select the `White Label` section.

## Step 2: The process of registering a new customer

After user authentication, to further utilize the sandbox, it is necessary to obtain the access_token.

To do this, open the `Sign up` section. 

Select **POST /v2/mobile/signup** and click `Try it out`.


> 📘 #### Then enter the following parameters and click the `Execute` button:
> 
> **Parameters**:
> 
> - [x] **X-Merchant-ID**: Use the X-Merchant-ID provided to you by your account manager.
> - [x] **X-Version**: 1.2  
>   **Request body**:
> - [x] **phone**: This is your existing phone number if it's already registered in the system, or a new phone number you want to use.
> - [x] **password**: This is your existing password if you already have an account, or a new password you want to set for your account.

## Step 3: Phone number confirmation

After registering a new customer, it is necessary to confirm the phone number. 

To do this, select **POST /v2/mobile/phone/confirm**, which is located in the same section and click `Try it out`.

> 📘 #### Then enter the following parameters and click the `Execute` button:
> 
> **Parameters**:
> 
> - [x] **X-Merchant-ID**: Use the X-Merchant-ID provided to you by your account manager.
> 
>   **Request body**:
> - [x] **phone**: The phone number provided during registration.
> - [x] **smsCode**: 1234 (Use only this SMS code)
> - [x] **fingerprint**: 1234444


Upon completing the request, an response with a status of 200 will be received, containing a data block, including the **access_token**.


## Step 4: Entering the access_token

Copy the obtained access_token and return to the **Available authorization** window.  
In the `Value` field, paste the copied **access_token** and click the `Authorize` button.



## Step 5: Using the sandbox

Now, after inputting the **access_token**, access to all requests in the sandbox is available.

You can employ the available requests to test the API and interact with the sandbox.
