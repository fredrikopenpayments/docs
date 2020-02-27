---
id: getconsentauthsubres
title: Get Consent Authorisation Sub-Resources
sidebar_label: Get Consent Authorisation Sub-Resources
---
```javascript
curl -X GET
    [API_HOST]/psd2/consent/v1/consents/[CONSENT_ID]/authorisations
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'PSU-IP-Address: [PSU_IP_Address]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
```

### Headers

See Create consent.

### Path parameter

- `CONSENT_ID`

### Response
```javascript
{
    "authorisationIds": [
        "[CONSENT_AUTH_ID]"
    ]
}
```

### Response headers

- `X-Request-ID`