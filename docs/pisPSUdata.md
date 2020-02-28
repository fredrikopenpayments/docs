---
id: pisPSUdata
title: Update PSU Data for Payment Initiation
sidebar_label: Update PSU Data for Payment Initiation
---
This endpoint is used to 
```javascript
curl -X PUT
    [API_HOST]/psd2/paymentinitiation/v1/payments/[PAYMENT_PRODUCT]/[PAYMENT_ID]/authorisations/[PAYMENT_AUTH_ID]
    -H 'Authorization: Bearer [ACCESS_TOKEN]'
    -H 'PSU-IP-Address: [PSU_IP_ADDRESS]'
    -H 'X-BicFi: [BICFI]'
    -H 'X-Request-ID: [GUID]'
    -d '{
        "authenticationMethodId": "[AUTHENTICATION_METHOD_ID]"
    }'
```

### Headers

- `PSU-IP-Address` is the IP address of the end user.
- `X-BicFi` the BICFI for the user's ASPSP. Find it in [the ASPSP API](/en/openpayments-NextGenPSD2-1.3.3.html#tag/ASPSP-Information-Service-(ASPSPIS)).
- `X-Request-ID` used to verify that the response matches the request.

### Path parameters

Get a `PAYMENT_ID` in the [Create payment initiation](createpaymentinitiation.md) resource. 

### Response
```javascript
{
    "chosenScaMethod": {
        "authenticationType": "PUSH_OTP",
        "authenticationMethodId": "[AUTHENTICATION_METHOD_ID]"
    },
    "_links": {
        "scaOAuth": {
            "href": "[AUTH_HOST]/connect/authorize?client_id=[CLIENT_ID]&scope=paymentinitiation&response_type=code&redirect_uri=[TPP_REDIRECT_URI]&state=[TPP_STATE]&acr_values=idp:[BICFI]%20paymentId:[PAYMENT_ID]%20paymentAuthorisationId:[PAYMENT_AUTH_ID]"
        }
    },
    "scaStatus": "scaMethodSelected"
}
```

### Response headers

- `X-Request-ID`
- `ASPSP-SCA-Approach` - see [below](#aspsp\-sca\-approach) for different values.

### Test procedure

If the ASPSP uses OAuth:
- The above endpoint returns an OAuth authorize URL in the `scoOAuth` field. 
- Replace all the bracketed fields with real values. In your code you will have to replace only the two TPP values.
    - `TPP_REDIRECT_URI` should be the URL to redirect to after auth is completed.
    - `TPP_STATE` can be anything the TPP wants.
    - `BICIFI`
- Run it in a browser. In this case you will get to a page at the ESSESESS sandbox. It may differ for different banks.
- In the page you get to you can use one of the following fake personal numbers:
    - 9311219639
    - 9311219589
    - 8811215477
    - 8811212862
    - 8311211356
- When you submit the data you will be redirected to the `[TPP_REDIRECT_URI]`
- On this URI a `code` param will be added. 
- Use this `code` in the subsequent call when getting the account information token.

Call the OAuth token endpoint to finalize payment.
```javascript
curl -X POST
    [AUTH_HOST]/connect/token
    -H 'Content-Type: application/x-www-form-urlencoded'
    -H 'X-PaymentAuthorisationId: [PAYMENT_AUTH_ID]'
    -H 'X-PaymentId: [PAYMENT_ID]'
    -d 'client_id=[CLIENT_ID]&client_secret=[CLIENT_SECRET]&code=[CODE]&redirect_uri=[TPP_REDIRECT_URI]&grant_type=authorization_code'
```