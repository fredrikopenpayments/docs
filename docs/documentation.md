---
id: documentation
title: Documentation
sidebar_label: Documentation
---
This documentation aims to give an understanding of the Open Payment platform and how to use the API services.
The used terminology is found in the [Glossary](glossary.md).

### Syntax
The character set is UTF 8 encoded. This specification is using the basic data elements "String", "Boolean", "ISODateTime", "ISODate", "UUID" and "Integer" 
(with a byte length of 32 bits) and ISO based code lists. 

Max35Text, Max70Text, Max140Text and Max500Text are defining strings with a maximum length of 35, 70, 140 and 500 characters respectively.
ASPSPs will accept for strings at least the following character set: 

a b c d ef g h i j k l m n o p q r s t u v w x y z
A B C D E F G H I J K L M N O P Q R S T U VW X Y Z 0 1 23 45 67 89
/-?:().,' +
Space

## Requests 
For API request calls, query parameters, HTTP header parameters and body content parameters are specified accordingly:

**Optional** 
The attribute is supported by the server, usage is optional for the client.

**Conditional** 
The attribute is supported by the server and might be mandated by the server provider in its own documentation of the support of this XS2A
interface or by certain rules as defined in the “Description” column of the table above.

**Mandatory** 
The attribute is supported by the server and shall be used by the client.

### X-Request-ID
All calls accept a header called `X-Request-ID` - this should be set to a newly generated guid. Denoted in the code with [GUID]. If your client is also a platform it would make sense to accept such an id from the client that calls you. This id is used to trace requests through our systems. Logging it somewhere together with the request will make troubleshooting much easier.

## Responses 
**Optional** The attribute is supported optionally by the server.

**Conditional** The attribute is supported by the server under certain conditions as indicated in the “Description” column of the table above.

**Mandatory** The attribute is always supported by the server.

