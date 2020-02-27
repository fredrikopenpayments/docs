---
id: aisgettransactionlist
title: Get Transaction List
sidebar_label: Get Transaction List
---
Retreive transactions for a given [ACCOUNT_ID].
```javascript
curl -X GET
    [API_HOST]/psd2/accountinformation/v1/accounts/[ACCOUNT_ID]/transactions?bookingStatus=[BOOKING_STATUS]&dateFrom=[DATE_FROM]
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

- `ACCOUNT_ID` refers to `resourceId` in the response from [Get Account List](#get-account-list).

### Query parameters

- `bookingStatus` booked, pending, both.
- `dateFrom` is a date in `yyyy-MM-dd` format.
- `dateTo` is a date in `yyyy-MM-dd` format. Optional.

### Response
```javascript
{
    "transactions": {
        "booked": [
            {
                "transactionId": "[TRANSACTION_ID]",
                "transactionAmount": {
                    "currency": "SEK",
                    "amount": "4101.24"
                }
            }
        ],
        "pending": [
            {
                "transactionId": "[TRANSACTION_ID]",
                "transactionAmount": {
                    "currency": "SEK",
                    "amount": "105"
                }
            }
        ],
        "_links": {
            "account": "/psd2/accountinformation/v1/accounts/[ACCOUNT_ID]"
        }
    },
    "balances": []
}
```

### Response headers

- `X-Request-ID`