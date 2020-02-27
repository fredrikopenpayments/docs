---
id: aspsp
title: How to use ASPSP
sidebar_label: How to use ASPSP
---
This API is used to retreive information about supported ASPSPs. Parts of the ASPSP information can be used to call the other APIs.

## Prerequisites
## Get an access token for ASPSP IS
```javascript
curl -X POST
    [AUTH_HOST]/connect/token
    -H 'Content-Type: application/x-www-form-urlencoded'
    -d 'client_id=[CLIENT_ID]&client_secret=[CLIENT_SECRET]&scope=aspspinformation&grant_type=client_credentials'
```

This post will return a JSON object that looks like this:
```javascript
{
    "access_token": "[ACCESS_TOKEN]",
    "expires_in": 3600,
    "token_type": "Bearer",
    "scope": "aspspinformation"
}
```
Bring the ACCESS_TOKEN forward to subsequent calls.

## Basic flow 
This is an example of a typical flow of the ASPSPIS in the system:
1. You are presented a list of supported countries.
1. You select a country.
1. The system retrieves a list of banks for that country.
1. You select a bank.
1. The system moves on to one of the other APIs to get account information or to initiate a payment.

## Account Servicing Payment Service Provider (ASPSP) Flow
![PlantUML model](/img/aspsp.svg)