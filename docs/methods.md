---
id: methods
title: Concepts
sidebar_label: Concepts
---
# Concepts

Open Payments supports dedicated payment authorisation endpoints for payment initiation transactions.
Consent transactions are established to handle transaction authorisation by the PSU. 

* multiple level SCA, where a transaction needs an authorisation by more than one PSU, e.g. in a corporate context

* signing of a group of transactions with one SCA, as it is offered by ASPSPs today in online banking

* signing of a group of transactions with multi-level SCA, where this group of transactions need an authorisation by more than one PSU, e.g. in a corporate context

To support this, the resources resulting from the submission of payment data or consent data are separated from authorisation (sub-)resources. A payment to be signed n times  will end up in a payment resource with n SCA (sub-)resources.