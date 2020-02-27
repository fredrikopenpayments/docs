---
id: pisgetpaymentinitiationstatus
title: Get Payment Initiation Status
sidebar_label: Get Payment Initiation Status
---
```javascript
curl -X GET
    [API_HOST]/psd2/paymentinitiation/v1/payments/[PAYMENT_PRODUCT]/[PAYMENT_ID]/status
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'PSU-IP-Address: [PSU_IP_ADDRESS]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
```

### Headers

- `PSU-IP-Address` is the IP address of the end user.
- `X-BicFi` the BICFI for the user's ASPSP. Find it in [the ASPSP API](/en/openpayments-NextGenPSD2-1.3.3.html#tag/ASPSP-Information-Service-(ASPSPIS)).
- `X-Request-ID` used to verify that the response matches the request.

### Path parameters

`PAYMENT_ID` that was returned from the initiation request.

### Response
```javascript
{
    "transactionStatus": "ACTC"
}
```

### Response headers

`X-Request-ID`