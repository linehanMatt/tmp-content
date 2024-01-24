---
title: 'What is a UID2 in the advertising industry?'
description: 'UID2s are identifiers generated from hashed emails/phone numbers that enable the advertising industry to speak a common language while respecting user privacy choices'
lastUpdated: '2023-01-27T20:07:13.873Z'
tags: ['Data Egress Through Connector Apps', 'The Trade Desk']
---
The UID2 is a unique user identifier that is used in the ad tech industry to match and link data from different sources. It is a key tool, generated and maintained by a consortium of Identity companies and organizations, that enables advertisers to create a comprehensive view of their audience and to reach them more effectively across multiple devices and platforms, without compromising consumer privacy. While The Trade Desk (TTD) is both an operator and an administrator of the UID2, they are not the only operator/administrator, and they do not own the ID (rather it is a combined effort of the Identity Consortium.) 

From the UID2 [spec](https://github.com/IABTechLab/uid2docs):

> The UID2 framework enables logged-in experiences from publisher websites, mobile apps, and Connected TV (CTV) apps to monetize through programmatic workflows. Built as an open-source, standalone solution with its own unique namespace, the framework offers the user transparency and privacy controls designed to meet local market requirements.

Narrative is proud to participate in this important Advertising industry initiative to help create an open source privacy-safe standard for user identity.

Narrative can automatically generate UID2’s based on the data that you upload. Currently supported data attributes are:

*   Hashed Email
*   SHA256 Hashed Email
*   Phone Number
*   SHA256 Hashed Phone Number.

In order to generate a UID2, you simply need to deliver data to the TTD Connector from within the Narrative platform that includes one of the above attributes; Narrative will handle the rest. For further instructions, see _**How do I get started with the TTD 3P Connector App**_?

If you already have converted your data to UID2s or are capturing UID2s from another source such as an advertising partner, our TTD Connector can seamlessly accept this data as well. Simply upload a dataset containing UID2s and Narrative will automatically map the field on your behalf.

You can read more about UID2 [here](https://www.thetradedesk.com/us/about-us/industry-initiatives/unified-id-solution-2-0). 

For more information on utilizing UID2s on the Narrative platform, or if you want to read more about TTD connector, see [What is the Narrative TTD Connector App?](https://kb.narrative.io/what-is-the-narrative-ttd-connector)
