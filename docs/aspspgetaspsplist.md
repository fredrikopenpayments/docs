---
id: aspspgetaspsplist
title: Get ASPSP List
sidebar_label: Get ASPSP List
---

```javascript
curl -X GET
    [API_HOST]/psd2/aspspinformation/v1/aspsps
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'X-Request-ID: [GUID]'
```

### Query parameters

- `isoCountryCodes` a comma separated list of countries to retrieve ASPSPs for. Optional.
- `cityIds` a comma separated list of city ids to retrieve ASPSPs for. Optional.

The service will return all matches for the queries. So it is possible to get all ASPSPs in Sweden and Helsinki by sending in the country code for Sweden and the city id for Helsinki.

### Response
```javascript
{
    "aspsps": [
        {
            "bicFi": "ESSESESS",
            "name": "Skandinaviska Enskilda Banken AB ",
            "logoUrl": "https://openbankingplatform.blob.core.windows.net/image/ESSESESS.png"
        },
        {
            "bicFi": "NDEASESS",
            "name": "Nordea Bank AB",
            "logoUrl": "https://openbankingplatform.blob.core.windows.net/image/NDEASESS.png"
        },
        {
            "bicFi": "HANDSESS",
            "name": "Handelsbanken",
            "logoUrl": "https://openbankingplatform.blob.core.windows.net/image/HANDSESS.png"
        }
    ]
}
```