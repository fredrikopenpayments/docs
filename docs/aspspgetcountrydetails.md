---
id: aspspgetcountrydetails
title: Get Country Details
sidebar_label: Get Country Details
---
This endpoint is used to get ASPSP details by entering the ``isoCountryCode``, which can be fetched from [Get Country List](aspspgetcountrylist.md).
```javascript
curl -X GET \
    [API_HOST]/psd2/aspspinformation/v1/countries/[COUNTRY_CODE]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'X-Request-ID: 6ff9e7ee-2ac2-42d3-a188-c7314d434b9c'
```

### Path parameter

`COUNTRY_CODE` 

### Response
```javascript
{
    "isoCountryCode": "SE",
    "name": "Sweden"
}
```