---
id: theapis
title: The APIs
sidebar_label: The APIs
---
Open Payments provides three building blocks on which you can build you bank aware application.

### [Account Servicing Payment Service Providers - ASPSPIS](aspsp.md)

This set of APIs makes it possible to discover what banks that are available for a certain country and what capabilities those banks have in the Open Payments ecosystem. 

### [Consent service](consent.md)

Then we have Account Information where it is possible to list all accounts for a [PSU](glossary.md) (Payment Service User),
get detailed account information and list transactions. 

The account APIs work together with the consent API to form a building block in your application. Read more in the and [accounts tutorial](ais.md).

### [Payment Initiation Service - PIS](aspsp.md) 

Payment Initiation where actual payments are initiated. This API uses its own idea about consent in concordance with the NextGen specification. 
So it is not possible to get a consent for payments from the consent APIs. 
Read more about how to initiate a payment in the [payment initiation tutorial](pis.md).

-   [ASPSP](/en/openpayments-NextGenPSD2-1.3.3.html#tag/ASPSP-Information-Service-(ASPSPIS))

-   [Consent](/en/openpayments-NextGenPSD2-1.3.3.html#tag/Consent-Service)

-   [Account
    Information](/en/openpayments-NextGenPSD2-1.3.3.html#tag/Account-Information-Service-(AIS))

-   [Payment
    Initiation](/en/openpayments-NextGenPSD2-1.3.3.html#tag/Payment-Initiation-Service-(PIS))

We plan to support other standards in this field in the future - let us know your needs and we can have a dialogue about how to make it happen.

Supported Banks
The supported banks area 

[supported banks](banks.md). initiate payments, transfer of funds and collect payment data for your clients – with their approval of course.