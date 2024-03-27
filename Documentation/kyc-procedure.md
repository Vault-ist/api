---
title: "KYC Procedure"
slug: "kyc-procedure"
excerpt: "Know Your Customer ([KYC](https://vault-bxou.readme.io/reference/kyc) procedures are an integral part of financial services and are designed to protect financial institutions from fraud, corruption, money laundering, and terrorist financing."
hidden: false
createdAt: "Tue Mar 19 2024 16:21:35 GMT+0000 (Coordinated Universal Time)"
updatedAt: "Wed Mar 20 2024 16:44:56 GMT+0000 (Coordinated Universal Time)"
---
The essence of the KYC procedure includes:

- Establishing the customer's identity.
- Understanding the nature of the customer's activities and confirming the legality of the source of funds.
- Assessing the risks of money laundering associated with the customer.

Upon successful completion of the verification, the customer is provided with the required service.

## The KYC COMMON Process Procedure

To complete the COMMON KYC, we collaborate with our partner Ondato and utilize their SDK.

You can find integration information for the web SDK on the WEB SDK integration page in the Ondato documentation.

The `COMMON` KYC process comprises the following steps:

### Step 1: Integration Phase

Installation of the Ondato library.

To install the Ondato library in your project, npm can be utilized. The installation command is as follows:

```bash bash
npm install @ondato-public/idv-sdk
```

Subsequently, the library will be accessible in your project.

Further details regarding library installation are available available [here](https://ondato.atlassian.net/wiki/spaces/PUB/pages/2393604111/Customer+Onboarding+Web+SDK+integration+v1#2%EF%B8%8F⃣-npm-(React-example)%3A).

### Step 2: Initiating the KYC Process

This phase commences with sending a request to the specified endpoint [POST /v4/kyc/start](https://vault-bxou.readme.io/reference/start) with the parameter `COMMON`. 

In response, the system generates a unique application identifier (**ID**).

### Step 3: Sending Data to Ondato

The unique application identifier (**ID**) generated in the preceding step is forwarded to Ondato alongside the requisite data.

### Step 4: Commencing Work with Ondato

Upon receiving the unique application identifier (**ID**), employ the `load` method from @ondato-public/idv-sdk with the following parameters:

```javascript
{
  mode: process.env.MODE === "production" ? IdvSdkMode.Production : IdvSdkMode.Sandbox, // Depending on the environment
  onSuccess: (props) => Perform a request to https://crpt-backend-main-service.sandbox.testessential.net/swagger-ui/index.html?urls.primaryName=White%20label#/KYC/finished with the COMMON parameter and {identificationId: id} // id is from the POST request kyc/start
  onFailure: (props) => Perform a request to https://crpt-backend-main-service.sandbox.testessential.net/swagger-ui/index.html?urls.primaryName=White%20label#/KYC/finished with the COMMON parameter and {identificationId: id} // id is from the [POST request kyc/start]
}
```

### Step 5: Returning the `load` Method

The `load` method returns `{begin: IdvSdkBegin; end: IdvSdkEnd;}`. 

After successfully loading the SDK, you can call the `begin` method with necessary parameters such as **idvId** (**ID** from the previous request), **retry**, and **language**.

```javascript
begin({
  idvId: id, // ID from the kyc/start request
  retry: false,
  language: "en-GB"
});

```

### Step 6: Confirmation Process from Ondato

Upon completion of the process at Ondato's end and successful verification, they return the application ID or other information confirming the successful completion of the process.

### Step 7: Completion of KYC Process

Upon receiving the application ID or confirmation from Ondato, a request is initiated to [POST /v4/kyc/ondato/finished](https://vault-bxou.readme.io/reference/finish), indicating the completion of the KYC process at Ondato's end.

### Step 8: Manual Confirmation

The KYC process always involves manual approval of the application after passing the verification process at Ondato's end. 

After completing this stage, the KYC process will be fully completed, and the client will have successfully undergone KYC.

## Working with the Ondato SDK in a Flutter application

The application utilizes the Ondato Flutter SDK from the official [repository](https://github.com/ondato/ondato-sdk-flutter).

<!-- theme: info -->

> These steps are applicable for both passing KYC `COMMON` and for `CARD PROGRAM 1`.

### Step 1: Integration Stage

Refer to the official documentation for dependency installation and SDK integration:

- [for Flutter](https://github.com/ondato/ondato-sdk-flutter)
- [for iOS](https://github.com/ondato/ondato-sdk-ios)
- [for Android](https://github.com/ondato/ondato-sdk-android)

### Step 2: Initiating the KYC Process

This stage begins with sending a request to the specified endpoint [POST /v4/kyc/start](https://vault-bxou.readme.io/reference/start) with the parameter `WALETTO`.  
In response, the system generates a unique application identifier (ID).

### Step 3: Initializing Ondato Configuration

The unique application identifier (ID) generated in the previous step is forwarded to Ondato in the identificationId field, along with necessary data.

```dart dart
await OndatoFlutter.init(
  OndatoServiceConfiguration(
    identificationId: ID,
    mode: currentApiStage == ApiStage.develop
        ? OndatoEnvironment.test
        : OndatoEnvironment.live,
    flowConfiguration: OndatoFlowConfiguration(
      showSplashScreen: false,
    ),
  ),
);
```

### Step 4: Starting the Identification Process

The Ondato identification process occurs by calling the startIdentification function, which initiates the Ondato flow depending on the platform running the application.

```dart dart
var identificationId = await OndatoFlutter.startIdentification();
```

After completing the flow, the function will return the identificationId, which needs to be saved.

### Step 5: Completing the KYC Process

After completing the Ondato flow, a request to finish the KYC with the obtained identificationId from the SDK should be sent: [POST /v4/kyc/ondato/finished](https://vault-bxou.readme.io/reference/finish).

### Step 6: Manual Confirmation

The KYC process always involves manual approval of the application after completing the verification process at the end of Ondato.

Upon completing this stage, the KYC process will be fully concluded, and the client will have successfully undergone the KYC procedure.

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
