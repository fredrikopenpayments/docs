---
id: getconsent
title: Get Consent
sidebar_label: Get Consent
---
Once you have a consent you can use the id for that consent to get information about the consent.
```javascript
curl -X GET
    [API_HOST]/psd2/consent/v1/consents/[CONSENT_ID]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'PSU-IP-Address: [PSU_IP_Address]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
```

### Headers

- `PSU-IP-Address` is the IP address of the end user.
- `X-BicFi` the BICFI for the user's ASPSP. Find it in [the ASPSP API](aspsp.md).
- `X-Request-ID` used to verify that the response matches the request.

### Path parameter

- `CONSENT_ID` - the id that was returned when the consent was created.

### Response
```javascript
{
    "consentId": "[CONSENT_ID]",
    "access": {
        "accounts": [
            {
                "iban": "[CONSENT_IBAN]",
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
    "recurringIndicator": false,
    "validUntil": "2019-10-01",
    "frequencyPerDay": 100,
    "lastActionDate": "2019-05-16",
    "consentStatus": "received"
}
```

This is the exact same body as the one sent in to the create consent request endpoint except that the current status is added.

### Response headers

- `X-Request-ID`