This endpoint is designed to retrieve a simplified list of operations from the catalog. The catalog of operations may include various actions available for execution within the system.

### Operation Information

- **name**: string  
  The name of the operation. All available operations in the Vault can be viewed [here](https://vault-bxou.readme.io/docs/operations-and-constraints).

- **constraint**: string  
  Constraints or requirements associated with performing the operation. Can be one of the following:
  - `NONE`: Indicates that there are no specific constraints or requirements associated with the operation. The operation is allowed without any additional conditions.
  - `DISABLED`: Indicates that the operation is currently disabled or not allowed. Users attempting this operation may be restricted.
  - `MAINTENANCE`: Indicates that the operation is under maintenance, and it may not be available for execution during this period. Users are advised to wait until maintenance is complete.

- **kycLevelPermissibleList**: array[string]  
  KYC levels for which this operation is permissible.

- **supportedVersion**: string  
  The version of the supported operation.

### Soft Update Information

- **Description**: string  
  This type of update is only related to functional features and is not mandatory for all users.

- **When the check occurs**: string  
  The check occurs when accessing a specific function.

- **How the check is performed**: string  
  If the version of the feature on the client is less than the required one, using this feature becomes impossible.

- **Actions upon check**: string  
  - If the feature is isolated, a modal window appears with a proposal to update the application.
  - If the feature is not isolated (for example, screens with tabs for features), instead of the feature's starting screen, a screen appears with a message about the need to update.
