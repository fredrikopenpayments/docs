---
id: parameters
title: Parameters
sidebar_label: Parameters
---
This section contains all relevant parameters with additional descriptions in alphabetic order.

### Headers
| Parameter | Description |
| --- | --- |
| `Consent-ID` | identification of the corresponding consent granted by the PSU |
| `PSU-IP-Address`  | is the IP-address of the end user |
| `X-BicFi` | is the identifier for the user's ASPSP. Find it in  the [ASPSP API](aspsp.md). |
| `X-Request-ID`  | is used to verify that the response matches the request |
           
### Path parameters

| Parameter | Description |
| --- | --- |
| `ACCOUNT_ID` | refers to `resourceId` in the response from [Get Account List](aisgetaccountlist.md) |
| `CITY_ID`  | is one of the IDs returned from the [Get City List](aspspgetcitylist.md) endpoint. |
| `COUNTRY_CODE` | is one of the codes in the ISO 3166-1 alpha-2 standard. |

### Query parameters
| Parameter | Description |
| --- | --- |
| `BICFI` | ASPSP identifier. You can get bank details by entering the BicFi code. Get the BicFi code from the [Get ASPSP List](aspspgetaspsplist.md) resource. |
| `cityIds` | Boolean, include balances in response. Optional. |
| `isoCountryCodes` | a comma separated list of countries to retrieve ASPSPs for. Optional. |
| `withBalance` | a comma separated list of city ids to retrieve ASPSPs for. Optional. |

## Responses
| Parameter | Description |
| --- | --- |
| `ASPSP-SCA-Approach` | --- |
| ``companyNumber`` | The company number is equivalent to the organisation number. |
| ``globalPaymentProducts`` | The  are supported by Open Payments for all banks. For more information about the supported payment products, see [payment products](paymentproducts.md). Note! The ``paymentProducts`` are supported, but needs to be configured accourding to the bank´s documentation. |
| ``supportedAuthorizationMethods`` | The  refers to the Open Payments authorisation method and environment. |
| `X-Request-ID` | --- |
