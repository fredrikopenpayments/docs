---
id: aspspgetcitydetails
title: Get City Details
sidebar_label: Get City Details
---

```javascript
curl -X GET
    [API_HOST]/psd2/aspspinformation/v1/cities/[CITY_ID]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'X-Request-ID: [GUID]'
```

### Path parameter

`CITY_ID` should be one of the ids returned from the "get cities" endpoint.

### Response
```javascript
{
    "cityId": "37efa883-c8ad-4ff7-927b-b11b02beb923",
    "name": "Stockholm",
    "isoCountryCode": "SE"
}
```

This is exactly as one item in the list returned from the "get cities" endpoint.