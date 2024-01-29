---
title: 'How do I cookie sync with Narrative?'
description: 'Often time browser-based identifiers are stored in domain-specific cookies. For domains to cross-reference those identifiers, a "cookie sync" needs to be established.'
lastUpdated: '2021-08-12T15:22:44.195Z'
tags: ['Integrations & Technical Guides', 'Narrative Syncs & Processes']
---
### Overview

Cookies are used to create a semi-persistent identifier for a particular computer's browser. Web browsers enforce a rule that a cookie that is set by a domain (ex: [example.com](http://example.com)) can only be read within that same domain. This rule means that different companies typically have different cookie-based identifiers.

To share identifiers that live in their own namespaces, we leverage cookie syncing, by passing the IDs as query parameters to create a shared understanding.

Currently, Narrative only supports partners initiating the sync with us.

### Partner Initiated Syncs

For partners who are initiating the sync with Narrative the following endpoint and query parameters can be used:

#### **Endpoint**

//io.narrative.io/?

#### Query Parameters

_**Parameter**_

_**Description**_

_companyId_: (Required) A unique ID assigned to the partner by Narrative

_id_: (Required) Type and Value of the identifier formatted as _partner\_id\_type:partner\_id\_value_. For cookies, the _partner\_id\_type_ will be assigned to the partner by Narrative

_red_: (Optional) If the partner would like Narrative to redirect back to the partner with the Narrative ID a properly encoded URL can be used

#### Example

BrandA would like to initiate a cookie sync with Narrative.

* companyID: 789
* customerID is \[123456789\]

Pixel before: io.narrative.io/?companyId=**XXX**&id=customer\_id:\[\[**XXX**\]\]

Pixel after: io.narrative.io/?companyId=**789**&id=**brandA\_id**:\[\[**123456789**\]\]

#### Macros

_${narrative.id.value}_: On the redirect parameter this macro will be replaced with the Narrative cookie identifier.

#### Example URL

//io.narrative.io/?companyId=**789**&id=**brandA\_id**:**123456789**&red=https%3A%2F%2Fexample.com%2F%3Fnarrative\_id%3D%24%7Bnarrative.id.value%7D
