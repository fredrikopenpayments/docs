---
id: paymentproducts
title: Payment products
sidebar_label: Payment products
---
A payment initiation to the bank is sent with a JSON body.

The following payment products are supported:
* sepa-credit-transfers
* instant-sepa-credit-transfers
* target-2-payments
* cross-border-credit-transfers

The request body depends on the payment-service:
* payments - a single payment initiation request
* bulk-payments - a collection of payment iniatiation requests
* periodic-payments

## Single and mulitilevel SCA Processes
The Payment Initiation Requests are independent from the number of payment authorisations. But the response messages are specific to either one SCA processing or multilevel SCA processing.

## Payment initiation with multilevel SCA
This specification requires an explicit start of the authorisation, i.e. links directly associated with SCA processing 
Example: 'scaRedirect' or 'scaOAuth' cannot be contained in the response message of a Payment Initation Request for a payment, where multiple authorisations are needed. 

IF any data is needed for the next action, like selecting an SCA method is not supported in the response, since all starts of the multiple authorisations are fully equal. In these cases, first an authorisation sub-resource has to be generated following the 'startAuthorisation' link.