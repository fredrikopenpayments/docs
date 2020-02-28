---
id: getconsentauthSCA
title: Get Consent Authorisation SCA Status
sidebar_label: Get Consent Authorisation SCA Status
---
This endpoint gets the status of a consent sub-resource authorisation. 

A sub-resource can be explained as a sub-transaction to handle PSU transactions authorisations with multiple transactions. A payment to be signed ***n*** times will end up in a payment resource with ***n*** SCA (sub-)resources. This applies for:

* multiple level SCA, where a transaction needs an authorisation by more than one PSU

* signing of a group of transactions with one SCA

* signing of a group of transactions with multi-level SCA, with authorisation by more than one PSU

```javascript
curl -X GET
    [API_HOST]/psd2/consent/v1/consents/[CONSENT_ID]/authorisations/[CONSENT_AUTH_ID]
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

Get the `CONSENT_ID` from the [Get consent](getconsent.md) resource.

Get the `CONSENT_AUTH_ID`from the [Start consent authorisation process](startconsentauthprocess.md) resource.

### Response
```javascript
{
    "scaStatus": "started"
}
```
``scaStatus``  has one of the following values:
* received
* psuIdentified
* psuAuthenticated
* scaMethodSelected
* started
* finalised
* failed
* exempted

### Response headers

`X-Request-ID`