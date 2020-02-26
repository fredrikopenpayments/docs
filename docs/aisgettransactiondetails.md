---
id: aisgettransactiondetails
title: Get Transaction Details
sidebar_label: Get Transaction Details
---
Retreive transaction details for a given [ACCOUNT_ID] and [TRANSACTIONID].
```javascript
curl -X GET
    [API_HOST]/psd2/accountinformation/v1/accounts/[ACCOUNT_ID]/transactions/[TRANSACTIONID]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'Content-Type: application/json'
    -H 'PSU-IP-Address: [PSU_IP_Address]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
    -H 'Consent-ID: [CONSENT_ID]'
```

### Headers

See Read account list.

### Path parameter

- `ACCOUNT_ID` refers to `resourceId` in the response from [Get Account List](#get-account-list).
- `TRANSACTION_ID` refers to `TRANSACTION_ID` in the response from [Get Transaction List](#get-transaction-list).

### Response
```javascript
{
    "transactionId": "[TRANSACTION_ID]",
    "transactionAmount": {
        "currency": "SEK",
        "amount": "4101.24"
    },
    "creditorAccount": {
        "iban": "[CREDITOR_IBAN]",
        "bban": "[CREDITOR_BBAN]"
    },
    "debtorAccount": {
        "iban": "[DEBTOR_IBAN]",
        "bban": "[DEBTOR_BBAN]"
    },
    "remittanceInformationUnstructured": "Short msg",
    "purposeCode": "OTHR"
}
```

### Response headers

- `X-Request-ID`

## Schemas

### Account status

`status` for an account can be one of the following values:

- enabled
- deleted
- blocked

### Account usage

`usage` for an acounnt Can be one of the following values:

- PRIV
- ORGA

### Balance type

`balanceType` can be one of the following values:

- closingBooked
- expected
- authorised
- openingBooked
- interimAvailable
- interimBooked
- forwardAvailable
- nonInvoiced

### Purpose code

`purposeCode` values for transactions can be found in the ISO 20022 External Code List ExternalCodeSets_1Q2018 June 2018.