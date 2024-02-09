---
title: 'What is an ID Type?'
description: 'Many data types contain unique identifiers.  The ID type denotes the class of identifier that is present within a record.'
lastUpdated: '2023-04-14T17:29:20.794Z'
tags: ['Data Types', 'General Attributes']
---
### Overview

Most data records in Narrative's Data Streaming Platform have one or more identifiers as an attribute. Identifiers act as a unique representation of an underlying concept. As an identifier can represent different concepts, all identifiers come with an identifier type (ID type), so the concept that the identifier is representing can be determined.

### ID Type Categories

The most common concept that identifiers are used for is to represent where the data was collected. The context of the collection often represents an ecosystem or API that allowed the data to be collected in the first place. A web browser, mobile phone, email, or other device are common data collection ecosystems.

#### Cookies

When data is collected within a web browser (both desktop and mobile) context the ID type associated with the identifier is usually a cookie. Cookies are storage mechanisms that are associated with a web browser and are specific to the domain where the data was collected. As such, Narrative does not have a "cookie" id type, but instead, the ID type is specific to the seller.

#### MAIDs

Mobile Ad Identifiers (MAIDS) are identifiers that are tied to a specific device and can be accessed through the APIs.  When data is collected via this mechanism, it will have a corresponding ID Type for the operating system where it was collected.  The most prevalent MAIDs are:

* _idfa_:  The ID Type for data collected via Apple's iOS.
* _adid_: The ID Type fo data collected via Google's Android

#### Hashed Emails

Some data records are associated with a user's email address.  Emails are considered Personally Identifiable Information (PII).  In order to pseudonymize the e-mails, making them non-PII, they are hashed at the source of the data collection.  Hashing creates an irreversible string that uniquely represents the email address without being able to see or use the underlying email address.  There are three prevalent hashing methodologies used:

* _md5\_email_: The email is lowercased and then hashed using the [MD5](https://en.wikipedia.org/wiki/MD5) hashing algorithm.
* _sha1\_email_: The email is lowercased and then hashed using the [SHA-1](https://en.wikipedia.org/wiki/SHA-1) hashing algorithm.
* _sha256\_email_: The email is lowercased and then hashed using the [SHA-2](https://en.wikipedia.org/wiki/SHA-2) hashing algorithm with a 256-bit digest.
