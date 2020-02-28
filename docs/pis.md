---
id: pis
title: How to use PIS 
sidebar_label: How to use PIS
---
This service is used to initiate payments. 

## Prerequisites
### Get an access token for Payment Initiation
Get a token to use for subsequent calls to the API. The scope is set to `paymentinitiation`.
```javascript
curl -X POST
    [AUTH_HOST]/connect/token
    -H 'Content-Type: application/x-www-form-urlencoded'
    -d 'client_id=[CLIENT_ID]&client_secret=[CLIENT_SECRET]&scope=paymentinitiation&grant_type=client_credentials'
```

This post will return a JSON object that looks like this:
```javascript
{
    "access_token": "[ACCESS_TOKEN]",
    "expires_in": 3600,
    "token_type": "Bearer"
}
```
### Get consent for Payment Initiation
To access AIS you must first get a consent. See [create consent](consent.md) for more information.

Note! The consent from the consent service is only used to access AIS. PIS has its own consent procedure.

## Payment Initiation Services (PIS) Flow
![PlantUML model](/img/pis.svg)
