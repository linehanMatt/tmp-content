---
title: 'Accepted Data Types by the Narrative The Trade Desk Connector'
description: 'Overview of data types such as Hashed Email, Phone Number, UID2s, MAIDs, and cookies that can be pushed to The Trade Desk’s marketplace via Narrative’s Connector.'
lastUpdated: '2024-01-31'
tags: ['Data Egress Through Connector Apps', 'The Trade Desk']
---

The Narrative TTD Connector App enables businesses to enhance their advertising efforts by facilitating the transmission of various data types to The Trade Desk (TTD). This connector supports the following data categories:

- **UID2s (Unique Identifier 2):** Unique user identifiers created by the TTD Connector App for tracking and targeting advertisements across devices.
- **Hashed Email (SHA256):** Automatically converted into UID2s by the Connector before being transmitted to TTD.
- **Hashed Phone Numbers (SHA256):** Similar to emails, hashed phone numbers are converted into UID2s. Ensure phone numbers are in [E.164 format](https://en.wikipedia.org/wiki/E.164), e.g., +12345678901.
- **Raw Email:** The Connector hashes and converts raw emails into UID2s for TTD.
- **Raw Phone Number:** Similar to raw emails, raw phone numbers are hashed and converted by the Connector.
- **MAIDs (Mobile Advertising IDs):** Unique identifiers for mobile devices, used for device-specific advertisement targeting.
- **TTD Cookies:** Directly utilized if collecting IDs from TTD via cookie sync. Narrative also offers cookie syncing services for matching your cookie IDs to TTD (contact your support representative for more information).

### Data Normalization and Hashing

It's crucial to adhere to UID2.0 guidelines for [normalization and hashing](https://unifiedid.com/docs/getting-started/gs-normalization-encoding) when preparing phone numbers and emails for transmission.

For more detailed information about utilizing the TTD Connector on the Narrative platform, refer to [What is the Narrative TTD Connector App?](https://kb.narrative.io/what-is-the-narrative-ttd-connector)
