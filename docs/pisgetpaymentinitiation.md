---
id: pisgetpaymentinitiation
title: Get Payment Initiation
sidebar_label: Get Payment Initiation
---
This endpoint is used to get a payment initiation. 
```javascript
curl -X GET
    [API_HOST]/psd2/paymentinitiation/v1/payments/[PAYMENT_PRODUCT]/[PAYMENT_ID]
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
Get a `PAYMENT_ID` in the [Create payment initiation](createpaymentinitiation.md) resource. 

### Response
```javascript
{
    "creditorAgent": "[BICFI]",
    "remittanceInformationUnstructured": "[MESSAGE]",
    "transactionStatus": "ACTC",
    "creditorAccount": {
        "iban": "[CREDITOR_IBAN]",
        "currency": "SEK"
    },
    "creditorName": "Enterprise Inc",
    "debtorAccount": {
        "iban": "[DEBTOR_IBAN]",
        "currency": "SEK"
    },
    "instructedAmount": {
        "currency": "SEK",
        "amount": "142.66"
    }
}
```

### Response headers

`X-Request-ID`