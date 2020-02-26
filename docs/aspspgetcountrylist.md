---
id: aspspgetcountrylist
title: Get Country List
sidebar_label: Get Country List
---

```javascript
curl -X GET
    [API_HOST]/psd2/aspspinformation/v1/countries
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'X-Request-ID: [GUID]'
```

### Query parameters

- `isoCountryCodes` a comma separated list of countries to retrieve. Optional.

### Response
```javascript
{
    "countries": [
        {
            "isoCountryCode": "SE",
            "name": "Sweden"
        },
        {
            "isoCountryCode": "FI",
            "name": "Finland"
        }
    ]
}
```

Where the country code and name will be according to the ISO 3166-1 alpha-2 standard.