---
id: methods
title: Concepts
sidebar_label: Concepts
---
Before you get started
-----------------
It is good to get acquainted with our terminology. 

The Open Payments Platform integrates with financial institutes, referred to as Account Servicing Payment
Service Providers (ASPSPs). As a developer you are referred to as a Third party Payment Provider (TPP) and the user is known as a Payment Services User (PSU).

## General notes about requests

### X-Request-ID

All calls accept the `X-Request-ID` header - this should be set to a newly generated guid. Denoted in the code with [GUID]. If your client is also a platform it would make sense to accept such an id from the client that calls you. This id is used to trace requests through our systems. Logging it somewhere together with the request will make troubleshooting much easier.

For more information, see [glossary](glossary.md).
## Scopes
### Strong Customer Authentication (SCA)
SCA mandates that two-factor authentication be performed on electronic payment transactions involving cards.

The following SCA scopes are supported:
* OAuth SCA scope - The TPP asks the PSU to authenticate. The TPP is given a URL of an OAuth 2 authorization endpoint hosted by the ASPSP.
* Redirect SCA scope - The TPP asks the PSU to authenticate. A predefined address is used to redirect the user to the ASPSP user interface, where the SCA is done between the PSU and the ASPSP. 
* Decoupled SCA scope - A predefined address is used to redirect the user to the ASPSP user interface, where the ASPSP asks the PSU to authenticate and the SCA is done between the PSU and the ASPSP.
