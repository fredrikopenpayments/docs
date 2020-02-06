---
id: getstarted
title: Quickstart
sidebar_label: Quickstart
---
## 1. Register

[Register a client](https://developer.openpayments.io) by creating a developer account at our [Developer Portal](https://developer.openpayments.io) to acquire client credentials.

You need to know what parts of the API you want access to for your new client:
ASPSP Information
Account Information
Payment Initiation

You will get a `client_id` and a `client_secret` that you can use to authenticate with the platform.

## 2. Authenticate
Open Payments Platform uses OAuth2 OpenID Connect for authentication.

Available `AUTH_HOST` values

| Environment | URL |
| --- | --- |
| Sandbox | https://auth.sandbox.openbankingplatform.com |
| Production | https://auth.openbankingplatform.com |

Available `API_HOST` values

| Environment | URL |
| --- | --- |
| Sandbox | https://api.sandbox.openbankingplatform.com |
| Production | https://api.openbankingplatform.com |


## 3. Integrate 

* ### Get started with [Postman](https://www.getpostman.com)

[Download](https://docs.openpayments.io/obp.postman_collection.json) our Postman Collection with ready made API calls. 

* ### Get started with the tutorials

* ### Read the APIs
Dig into the [APIs](http://localhost:3000/en/openpayments-NextGenPSD2-1.3.3.html)