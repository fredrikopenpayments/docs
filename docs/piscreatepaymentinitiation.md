---
id: piscreatepaymentinitiation
title: Create Payment Initiation
sidebar_label: Create Payment Initiation
---
```javascript
curl -X POST
    [API_HOST]/psd2/paymentinitiation/v1/payments/[PAYMENT_PRODUCT]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'Content-Type: application/json'
    -H 'PSU-IP-Address: [PSU_IP_ADDRESS]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
    -d '{
        "instructedAmount":
        {
            "currency": "SEK",
            "amount": "142.66"
        },
        "debtorAccount":
        {
            "iban": "[DEBTOR_IBAN]",
            "currency": "SEK"
        },
        "creditorName": "Enterprise Inc",
        "creditorAccount":
        {
            "iban": "[CREDITOR_IBAN]",
            "currency": "SEK"
        },
        "remittanceInformationUnstructured": "[MESSAGE]"
    }'
```

### Headers

- `PSU-IP-Address` is the IP address of the end user.
- `X-BicFi` the BICFI for the user's ASPSP. Find it in [the ASPSP API](/en/openpayments-NextGenPSD2-1.3.3.html#tag/ASPSP-Information-Service-(ASPSPIS)).
- `X-Request-ID` used to verify that the response matches the request.

### Path parameters

`PAYMENT_PRODUCT` can be one of:

- `domestic` - this is a non-euro payment within one country.
- `sepa-credit-transfers` - this is a EURO payment from one EURO ASPSP to another
- `international` - this is an international payment

The [Get ASPSP Details endpoint](/en/openpayments-NextGenPSD2-1.3.3.html#operation/getASPSPDetails) will tell you what payment products that are availalbe for that ASPSP.

### Response
```javascript
{
    "transactionStatus": "ACTC",
    "paymentId": "[PAYMENT_ID]",
    "_links": {
        "startAuthorisationWithTransactionAuthorisation": {
            "href": "/psd2/paymentinitiation/v1/payments/[PAYMENT_PRODUCT]/[PAYMENT_ID]/authorisations"
        },
        "self": {
            "href": "/psd2/paymentinitiation/v1/payments/[PAYMENT_PRODUCT]/[PAYMENT_ID]"
        },
        "status": {
            "href": "/psd2/paymentinitiation/v1/payments/[PAYMENT_PRODUCT]/[PAYMENT_ID]/status"
        }
    },
    "psuMessage": "Please confirm payment [PAYMENT_ID]"
}
```

### Response headers

`X-Request-ID`