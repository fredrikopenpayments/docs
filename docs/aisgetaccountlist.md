---
id: aisgetaccountlist
title: Get Account List
sidebar_label: Get Account List
---

```javascript
curl -X GET
    [API_HOST]/psd2/accountinformation/v1/accounts
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'Content-Type: application/json'
    -H 'PSU-IP-Address: [PSU_IP_Address]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
    -H 'Consent-ID: [CONSENT_ID]'
```

### Headers

- `PSU-IP-Address` is the IP address of the end user.
- `X-BicFi` the BICFI for the user's ASPSP. Find it in [the ASPSP API](aspsp.md).
- `X-Request-ID` used to verify that the response matches the request.
- `Consent-ID` identification of the corresponding consent as granted by the PSU.

### Response
```javascript
{
    "accounts": [
        {
            "resourceId": "[ACCOUNT_ID]",
            "iban": "[IBAN]",
            "bban": "[BBAN]",
            "currency": "SEK",
            "bic": "[BICFI]"
        }
    ]
}
```

### Response headers

- `X-Request-ID`