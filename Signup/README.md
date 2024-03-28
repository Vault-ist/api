<h2>Overview</h2>

The `SignUp` section in the Vault company is designed to provide functionality related to the registration of new users in the system. It offers methods that enable clients to create new user accounts, verify them, and retrieve information associated with the [registration process](https://github.com/crypterium-com/api-vault/wiki/Registration-Process).

## Check for IP and phone number prefix blocking

Upon registering a new user, a comprehensive check is carried out, including verification of the requesting IP address and the phone number prefix. This check occurs both on mobile devices (via the application), through the web interface, and via API.

### IP address verification

Before registration or authentication, the requesting IP address is checked. There is a table of forbidden countries (Forbidden Country) where countries with restricted access are listed. If the IP address belongs to a country listed in this table, the user will be unable to authenticate or register. Users whose IP addresses belong to a forbidden country will receive an appropriate error message.

### Phone number prefix verification

Phone numbers are also subject to verification to ensure compliance with allowed and forbidden countries (Forbidden Registration Country). If the phone number prefix corresponds to a country forbidden for registration, the user will receive a corresponding error message.

### Backend responses in case of errors

In case of violating one of the verification criteria (for example, a forbidden IP address or phone number prefix), the backend returns various error messages, including specific error codes for client-side processing convenience.

- `COUNTRY_BLOCKED_FOR_REGISTRATION (blocked by IP)`: If the requesting IP address belongs to a country included in the list of forbidden countries for registration, an error "We're sorry, but the application is not available in your region" with error code COUNTRY_BLOCKED_FOR_REGISTRATION will be returned.
- `PHONE_PREFIX_BLOCKED_FOR_REGISTRATION (blocked by phone number prefix)`: If the phone number prefix corresponds to a country forbidden for registration, an error "Registration is prohibited in your country" with error code PHONE_PREFIX_BLOCKED_FOR_REGISTRATION will be returned.

### Breakdown of error scenarios based on IP and phone number prefix considering the forbidden countries

1. From an allowed IP with an allowed phone number prefix: Response code 200.
2. From an allowed IP with a forbidden phone number prefix: Error message "Registration is prohibited in your country" with error code PHONE_PREFIX_BLOCKED_FOR_REGISTRATION.
3. From a forbidden IP with a forbidden phone number prefix: Error message "We're sorry, but the application is not available in your region" with error code COUNTRY_BLOCKED_FOR_REGISTRATION (since the IP check takes precedence).
4. From a forbidden IP with an allowed phone number prefix: Error message "We're sorry, but the application is not available in your region" with error code COUNTRY_BLOCKED_FOR_REGISTRATION.

## Forbidden countries for registration

- Abkhazia
- Afghanistan
- Albania
- Barbados
- Botswana
- Cambodia
- Crimea
- Cuba
- Donetsk National Republic (DNR)
- Gaza Strip
- Haiti
- Iran
- Iraq
- Jamaica
- Kashmir
- Libya
- Luhansk National Republic (LNR)
- Mongolia
- Myanmar
- Nagorno Karabakh
- Netherlands (the)
- Nicaragua
- North Korea (Democratic People's Republic of Korea)
- Pakistan
- Palestine
- Senegal
- Russia
- Somalia
- South Ossetia
- South Sudan
- Syria
- Trinidad and Tobago
- Uganda
- Vanuatu
- West Bank
- Yemen

## Registration process

![](https://files.readme.io/437b2d8-image.png)
