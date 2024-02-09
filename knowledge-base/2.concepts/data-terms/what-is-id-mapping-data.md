---
title: 'What are examples of ID mappings that Narrative offers?'
description: 'Review different ID linkages available to purchase in the Narrative Data Studio'
lastUpdated: '2023-04-24T22:50:05.298Z'
tags: ['Data Types', 'Identifier Mapping']
---
### Overview

When creating a quer in Data Studio, users choose between a variety of ID types that they want to make a connection to. ID Mapping buys will transact against suppliers who link two identifiers to a single user, such as email to a mobile phone. This data can be effectively used to expand targeting into different strategies like desktop, email and mobile.

### ID Types & Common Linkages

#### _Types_

#### **Hashed Email (HEM)**

md5, sha1, sha256

* Collected through newsletters, registrations & sign-ups, and other online properties where an email is entered or required
* Personal Identifiable Information (PII) is removed at the point of hashing

#### **Mobile Ad IDs (MAIDs)**

IDFA & AAID

* A unique pseudo-anonymous identifier tied to a mobile phone, often collected from developers through APIs offered on the device

#### **Cookies**

* Storage mechanism that are associated with a web browser (mobile web or desktop) and are specific to the domain of the collected data
* Specific to the domain of the data collected (Amazon different than Google)

#### _Common Linkages_

Below are examples of the types of ID Mapping Linkages available through a variety of suppliers in Narrative.

#### **Hashed Email<>MAID**

* Supplier has made a connection of (1) Hashed Email to (1) Mobile Advertising ID
* Example: user created an in-app login with an email address, since done within an app that MAID is collected as well, making the connection of HEM<>MAID

#### **Cookie<>MAID or Hashed Email**

* Narrative can provide cookie to MAID mappings by using supplier Cookie Syncs
* Narrative supports Suppliers that provide their own ID Mapping of their unique Cookie IDs to either hashed emails or MAIDs
  * Supplier cookie data is typically collected from a web browser when a user visits on a desktop or mobile device
  * A cookie is fired and that device is collected and both are mapped to each other
* To standardize different supplier mappings, Narrative creates their own cookie ID (Narrative Cookie) mapped to the additional identifier, as an email hash or MAID
* This allows different Cookie IDs from different Suppliers to be linked to a shared value in Narrative (Narrative Cookie)

### Want to learn more?

Contact your Partner Success Manager today or reach us at <partner-success@narrative.io> to learn more about how the Narrative platform can power your data strategy.
