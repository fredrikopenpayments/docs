---
id: pisgetpaymentinitiation
title: Get Payment Initiation
sidebar_label: Get Payment Initiation
---
```javascript
curl -X GET
    [API_HOST]/psd2/paymentinitiation/v1/payments/[PAYMENT_PRODUCT]/[PAYMENT_ID]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'PSU-IP-Address: [PSU_IP_ADDRESS]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
```

### Headers

See [Create Payment Initiation](#create-payment-initiation)

### Path parameters

`PAYMENT_ID` that was returned from the initiation request.

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