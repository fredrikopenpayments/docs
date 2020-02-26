---
id: onboarding
title: Onboarding
sidebar_label: Onboarding
---
### 1. Register
[Register a client](https://developer.openpayments.io) by creating a developer account at our [Developer Portal](https://developer.openpayments.io) to acquire client credentials.

You need to decide what API service you want your new client to access:
#### ASPSP Information Services (ASPSPIS)
* Account transaction reports - including balances
* Card transaction reports - including balances
* Account balances
* Card balances
* A list of available accounts 
* A list of available card accounts
* Account details
* Card account details

#### Account Information Service (AIS)
* Transaction reports for a given account or card account including balances if applicable.
* Balances of a given account or card account
* A list of available accounts or card account
* Account details of a given account or card account or of the list of all accessible accounts or card account relative to a granted consent

The following consent services are a part of the AIS:
* Create and authorize consent between the PSU and the TPP
* Get consent status 
* Get previously authorised consents

#### Payment Initiation Service (PIS)
* Initiate payments
* Update payments
* Get payment status information

You will get a `client_id` and a `client_secret` to authenticate with the platform.

### 2. Authenticate
Open Payments Platform uses OAuth2 OpenID Connect for authentication. 
You can use the APIs live or in our sandbox environment, which does not interact with the banking networks or affect your live data.

The API key you use to authenticate the request determines whether the request is live mode or in the sandbox.

Available `AUTH_HOST` values

| Environment | URL |
| --- | --- |
| Sandbox | https://auth.sandbox.openbankingplatform.com |
| Production | https://auth.openbankingplatform.com |

### 3. Integrate 
You can now start integrating with:
* [Postman](postman.md)
* [API ref](http://localhost:3000/en/openpayments-NextGenPSD2-1.3.3.html)

## Tutorials
* [ASPSP](aspsp.md)
* [Account Information Service](aspsp.md)
* [Consent](consent.md)
* [Payment Initiation Service](pis.md)