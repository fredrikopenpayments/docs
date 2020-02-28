---
id: getconsentauthsubres
title: Get Consent Authorisation Sub-Resources
sidebar_label: Get Consent Authorisation Sub-Resources
---
This endpoint gets identifiers, Consent IDs, of all generated authorisation sub-resources for consents. 

A sub-resource can be explained as a sub-transaction to handle PSU transactions authorisations with multiple transactions. A payment to be signed ***n*** times will end up in a payment resource with ***n*** SCA (sub-)resources. This applies for:

* multiple level SCA, where a transaction needs an authorisation by more than one PSU

* signing of a group of transactions with one SCA

* signing of a group of transactions with multi-level SCA, with authorisation by more than one PSU


```javascript
curl -X GET
    [API_HOST]/psd2/consent/v1/consents/[CONSENT_ID]/authorisations
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
    "authorisationIds": [
        "[CONSENT_AUTH_ID]"
    ]
}
```

### Response headers

- `X-Request-ID`

There are several Authorisation Sub-resources:

* in context of a Payment Initiation Request

GET /v1/{payment-service}/{payment-product}/{paymentId}/authorisations

* in context of an Account Information Consent Request

GET /v1/consents/{consentId}/authorisations

* in context of a Signing Basket Authorisation Request

GET /v1/signing-baskets/{basketId}/authorisations