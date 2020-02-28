---
id: aspspgetcountrylist
title: Get Country List
sidebar_label: Get Country List
---
This endpoint will get all ISO country codes per country, which can used to filter the ASPSP list.

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

The country code and name syntax is according to the ISO 3166-1 alpha-2 standard.