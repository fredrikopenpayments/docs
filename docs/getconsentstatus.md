---
id: getconsentstatus
title: Get Consent Status
sidebar_label: Get Consent Status
---
The consent request status is returned as part of the "get consent request" endpoint but it is also possible to use this endpoint to get only the status and nothing else. It is basaically the same call with `status` added at the end to the path.
```javascript
curl -X GET
    [API_HOST]/psd2/consent/v1/consents/[CONSENT_ID]/status
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

- `CONSENT_ID`

### Response
```javascript
{
    "consentStatus": "received"
}
```

See possible values for status [further down](#consent-status).

### Response headers

- `X-Request-ID`