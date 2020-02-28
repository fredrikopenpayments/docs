---
id: getconsentstatus
title: Get Consent Status
sidebar_label: Get Consent Status
---
This endpoint is used to get the status of the consent.

The consent request status is also returned as part of the [Get Consent](getconsent.md) endpoint.

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

-``X-Request-ID``

-``consentStatus`` for a consent can have one of the following values:
* received
* rejected
* valid
* revokedByPsu
* expired
* terminatedByTpp

### Response headers

