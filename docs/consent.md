---
id: consent
title: How to use Consent service
sidebar_label: How to use Consent service
---
This service is used to retreive and manage consent to access account information or perform payments.

### Get an access token for Account Information
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
## Consent Flow
![PlantUML model](/img/consent.svg)