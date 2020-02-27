---
id: schemas
title: Schemas
sidebar_label: Schemas
---
## Consent
### Consent status
`consentStatus` for a consent can be one of the following values:
- received
- rejected
- valid
- revokedByPsu
- expired
- terminatedByTpp

### Consent authorisation status
`scaStatus` for a consent authorisation can be one of the following values:
- received
- psuIdentified
- psuAuthenticated
- scaMethodSelected
- started
- finalised
- failed
- exempted

### ASPSP-SCA-Approach
This is a response header that describes how to proceed with authentication. 
Can be one of the following values. See the NextGen specs for more details.
- EMBEDDED
- DECOUPLED
- REDIRECT

### Authentication type
`authenticationType` for a consent authorisation can be one of the following values:
- SMS_OTP
- CHIP_OTP
- PHOTO_OTP
- PUSH_OTP
At this point the only type supported by banks are `PUSH_OTP` and how that works is covered by this tutorial. As we move into more markets and cover more different banks this will change and the documentation will be updated.

## AIS
### Account status
`status` for an account can be one of the following values:
- enabled
- deleted
- blocked

### Account usage
`usage` for an account can be one of the following values:
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

## PIS
### Transaction status
Read more about the potential values in the NextGen specification.

### ASPSP-SCA-Approach
This is a response header that describes how to proceed with authentication. 
Can be one of the following values. See the NextGen specs for more details.
- EMBEDDED
- DECOUPLED
- REDIRECT

### Payment authorisation status
`scaStatus` for a payment authorisation can be one of the following values:
- received
- psuIdentified
- psuAuthenticated
- scaMethodSelected
- started
- finalised
- failed
- exempted

### Authentication type
`authenticationType` for a payment authorisation can be one of the following values:
- SMS_OTP
- CHIP_OTP
- PHOTO_OTP
- PUSH_OTP

