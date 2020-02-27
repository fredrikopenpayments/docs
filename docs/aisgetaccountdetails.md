---
id: aisgetaccountdetails
title: Get Account Details
sidebar_label: Get Account Details
---
Use one of the [ACCOUNT_ID]s to get more information about a specific account.
```javascript
curl -X GET
    [API_HOST]/psd2/accountinformation/v1/accounts/[ACCOUNT_ID]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'Content-Type: application/json'
    -H 'PSU-IP-Address: [PSU_IP_Address]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
    -H 'Consent-ID: [CONSENT_ID]'
```
### Headers
- `PSU-IP-Address` - the IP-address of the end user
- `X-BicFi` - the identifier for the user's ASPSP. Find it in  the [ASPSP API](aspsp.md).
- `X-Request-ID` - used to verify that the response matches the request
- `Consent-ID` - identification of the corresponding consent granted by the PSU

### Path parameter
- `ACCOUNT_ID` - refers to `resourceId` in the response from [Get Account List](aisgetaccountlist.md).

### Query parameters
- `withBalance` Boolean, include balances in response. Optional.

### Response
```javascript
{
    "resourceId": "[ACCOUNT_ID]",
    "iban": "[IBAN]",
    "bban": "[BBAN]",
    "currency": "SEK",
    "cashAccountType": "[CASH_ACCOUNT_TYPE]",
    "status": "enabled",
    "bic": "[BICFI]",
    "usage": "PRIV",
    "balances": [
        {
            "balanceAmount": {
                "currency": "SEK",
                "amount": "33633.25"
            },
            "balanceType": "closingBooked",
            "creditLimitIncluded": false
        },
        {
            "balanceAmount": {
                "currency": "SEK",
                "amount": "33528.25"
            },
            "balanceType": "interimAvailable",
            "creditLimitIncluded": false
        }
    ]
}
```

### Response headers
- `X-Request-ID`