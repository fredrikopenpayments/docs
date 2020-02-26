---
id: ais
title: How to use the AIS API
sidebar_label: How to use the AIS API
---
This API is used to access information about accounts. Lists of accounts with an ASPSP and the actual transactions for one account. In order to be able to access this API first a consent needs to be acquired. See the [consent tutorial](consent.md) for how that is done.

## Basic flow 
This is an example of a typical flow of the ASPSPIS in the system:
1. You are presented a list of supported countries.
1. You select a country.
1. The system retrieves a list of banks for that country.
1. You select a bank.
1. The system moves on to one of the other APIs to get account information or to initiate a payment.

## Hosts
Available `AUTH_HOST` values
| Environment | URL |
| --- | --- |
| Sandbox | https://auth.sandbox.openbankingplatform.com |
| Production | https://auth.openbankingplatform.com |

Available `API_HOST` values
| Environment | URL |
| --- | --- |
| Sandbox | https://api.sandbox.openbankingplatform.com |
| Production | https://api.openbankingplatform.com |

## Account Information Services (AIS) Flow
![PlantUML model](/img/ais.svg)

## Acquire an access token for Account Information

Get a token to use for subsequent calls to the API. The scope should be set to `accountinformation`.
```javascript
curl -X POST
    [AUTH_HOST]/connect/token
    -H 'Content-Type: application/x-www-form-urlencoded'
    -d 'client_id=[CLIENT_ID]&client_secret=[CLIENT_SECRET]&scope=accountinformation&grant_type=client_credentials'
```

This post will return a JSON object that looks like this:
```javascript
{
    "access_token": "[ACCESS_TOKEN]",
    "expires_in": 3600,
    "token_type": "Bearer",
    "scope": "accountinformation"
}
```

## Acquire a consent

You'll need a valid consent for the ASPSP you want to interact with.
Follow instructions in [the Consent API](consent.md).

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