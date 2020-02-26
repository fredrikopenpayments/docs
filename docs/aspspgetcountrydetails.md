---
id: aspspgetcountrydetails
title: Get Country Details
sidebar_label: Get Country Details
---

```javascript
curl -X GET \
    [API_HOST]/psd2/aspspinformation/v1/countries/[COUNTRY_CODE]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'X-Request-ID: 6ff9e7ee-2ac2-42d3-a188-c7314d434b9c'
```

### Path parameter

The `COUNTRY_CODE` parameter should be one of the codes in the ISO 3166-1 alpha-2 standard.

### Response
```javascript
{
    "isoCountryCode": "SE",
    "name": "Sweden"
}
```

This is exactly the same as in the country list.