---
id: createconsent
title: Create Consent
sidebar_label: Create Consent
---
This endpoint is used to initiate the consent process with a request for consent.
```javascript
curl -X POST
    [API_HOST]/psd2/consent/v1/consents
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'Content-Type: application/json'
    -H 'PSU-IP-Address: [PSU_IP_Address]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
    -d '{
        "access": {
            "accounts": [
                {
                    "iban": "[CONSENT_IBAN]",
                    "currency": "[CONSENT_CURRENCY]"
                },
                {
                    "iban": "[OTHER_CONSENT_IBAN]",
                    "currency": "[CONSENT_CURRENCY]"
                }
            ],
            "balances": [
                {
                    "iban": "[CONSENT_IBAN]",
                    "currency": "[CONSENT_CURRENCY]"
                }
            ],
            "transactions": [
                {
                    "iban": "[CONSENT_IBAN]",
                    "currency": "[CONSENT_CURRENCY]"
                }
            ]
        },
        "recurringIndicator": [CONSENT_RECURRING_INDICATOR],
        "validUntil": "[yyyy-MM-dd]",
        "frequencyPerDay": [CONSENT_FREQUENCY_PER_DAY],
        "combinedServiceIndicator": [CONSENT_COMBINED_SERVICE_INDICATOR]
    }'
```

### Headers

- `PSU-IP-Address` is the IP address of the end user.
- `X-BicFi` the BICFI for the user's ASPSP. Find it in [the ASPSP API](aspsp.md).
- `X-Request-ID` used to verify that the response matches the request.

### Body description

`access` is a list of data items that consent need to be acquired for. There are three possible things to get consent from:

- `accounts` this is a consent to get access to an account list with some account details needed.
- `balances` this is a consent to get access to balances for accounts.
- `transactions` this is a consent to see all the transactions for accounts.

Each consent request contains `iban` and `currency` (optional). Each consent request can be a list of account ids (ibans).
The `balances` and `transactions` consent request must contain a subset of the accounts listed in `accounts`.

`recurringIndicator` is a boolean that indicates if the consent can be used multiple times or not.
`validUntil` is a date in `yyyy-MM-dd` format.
`frequencyPerDay` is a number indicating the number of usages per day for this consent.
`combinedServiceIndicator` if true this indicates that the session will be used to initate a payment also. It has no practical meaning at this time.

### Response
```javascript
{
    "consentStatus": "received",
    "consentId": "[CONSENT_ID]",
    "scaMethods": [
        {
            "authenticationType": "PUSH_OTP",
            "authenticationMethodId": "[AUTHENTICATION_METHOD_ID]"
        }
    ],
    "_links": {
        "self": {
            "href": "/psd2/consent/v1/consents/[CONSENT_ID]"
        },
        "status": {
            "href": "/psd2/consent/v1/consents/[CONSENT_ID]/status"
        },
        "startAuthorisation": {
            "href": "/psd2/consent/v1/consents/[CONSENT_ID]/authorisations"
        }
    }
}
```

At this point the returned status should always be `received`. All possible values are listed [below](#consent-status).

The list at `scaMethods` typically contains one entry. But in the future it is possible that banks - or our platform here - will support multiple methods.

Authentication type will always be `PUSH_OTP` since that is what the banks we integrate with support. In the future it may change. See [below](#authentication-type) for a list of possible types.

The list of links can be used for further actions on the consent. The `self` one is obviously to retreive the created consent request. The `status` is for accessing the status of the request. And `startAuthorisation`is the next step in the sequence of calls that is needed to get a consent.


### Response headers

- `ASPSP-SCA-Approach` see below for different values.
- `X-Request-ID`