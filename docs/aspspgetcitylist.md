---
id: aspspgetcitylist
title: Get City List
sidebar_label: Get City List
---

```javascript
curl -X GET
    [API_HOST]/psd2/aspspinformation/v1/cities
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'X-Request-ID: [GUID]'
```

### Query parameters

- `isoCountryCodes` a comma separated list of countries to retrieve cities for. Optional.
- `cityIds` a comma separated list of city ids to retrieve. Optional.

The service will return all matches for the queries. So querying for `SE` and `ba9dd929-1408-33a6-3ce2-bc45fcfaaa5c` will result in both Stockholm and Helsinki being returned.

### Response
```javascript
{
    "cities": [
        {
            "cityId": "37efa883-c8ad-4ff7-927b-b11b02beb923",
            "name": "Stockholm",
            "isoCountryCode": "SE"
        },
        {
            "cityId": "ba9dd929-1408-33a6-3ce2-bc45fcfaaa5c",
            "name": "Helsinki",
            "isoCountryCode": "FI"
        }
    ]
}
```