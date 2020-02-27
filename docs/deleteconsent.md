---
id: deleteconsent
title: Delete Consent
sidebar_label: Delete Consent
---
A consent request can be deleted with a `DELETE` call.
```javascript
curl -X DELETE
    [API_HOST]/psd2/consent/v1/consents/[CONSENT_ID]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'PSU-IP-Address: [PSU_IP_Address]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
```

### Status code

`204 No content`

### Response headers

- `X-Request-ID`