---
id: pisauthsubres
title: Get Payment Initiation Authorisation Sub-Resources
sidebar_label: Get Payment Initiation Authorisation Sub-Resources
---
This endpoint gets identifiers, Payment IDs, of all generated authorisation sub-resources for payments. 

A sub-resource can be explained as a sub-transaction to handle PSU transactions authorisations with multiple transactions. A payment to be signed ***n*** times will end up in a payment resource with ***n*** SCA (sub-)resources. This applies for:

* multiple level SCA, where a transaction needs an authorisation by more than one PSU

* signing of a group of transactions with one SCA

* signing of a group of transactions with multi-level SCA, with authorisation by more than one PSU

    curl -X GET
        [API_HOST]/psd2/paymentinitiation/v1/payments/[PAYMENT_PRODUCT]/[PAYMENT_ID]/authorisations
        -H 'Authorization: Bearer [ACCESS_TOKEN]'
        -H 'PSU-IP-Address: [PSU_IP_ADDRESS]'
        -H 'X-BicFi: [BICFI]'
        -H 'X-Request-ID: [GUID]'

### Headers

- `PSU-IP-Address` is the IP address of the end user.
- `X-BicFi` the BICFI for the user's ASPSP. Find it in [the ASPSP API](/en/openpayments-NextGenPSD2-1.3.3.html#tag/ASPSP-Information-Service-(ASPSPIS)).
- `X-Request-ID` used to verify that the response matches the request.

### Path parameters

Get the `PAYMENT_ID` from the [Create payment initiation](createpaymentinitiation.md) resource.

Get the `CONSENT_AUTH_ID`from the [Start consent authorisation process](startconsentauthprocess.md) resource.

`PAYMENT_ID` that was returned from the initiation request.

### Response
```javascript
{
    "authorisationIds": [
        "[PAYMENT_AUTH_ID"
    ]
}
```

### Response headers

- `X-Request-ID`