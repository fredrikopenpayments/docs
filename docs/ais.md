---
id: ais
title: How to use AIS
sidebar_label: How to use AIS
---
This service is used to access account information.
## Prerequisites
### Get an access token for Account Information
Get a token to use for subsequent calls to the API. The scope is set to `accountinformation`.
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
### Get consent
To access AIS you must first aquire a consent. See [create consent](consent.md) for more information.

## Account Information Services (AIS) Flow
![PlantUML model](/img/ais.svg)