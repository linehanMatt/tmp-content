---
title: 'How will Deduplication Settings affect my Data Studio Subscription?'
description: 'With Narrative''s advanced Deduplication, you can exclude irrelevant or redundant data from your subscription, even when buying from multiple Suppliers. Get only the data you need. Nothing more. '
lastUpdated: '2023-06-14T18:15:20.617Z'
tags: ['Buying Data', 'Data Studio']
---
### Sample **Digital Consumption** Data from the Narrative Marketplace

#### _Deduplication: NONE_

Narrative's Marketplace contains billions of rows of data from over 30 Suppliers. Certain rows of data will contain repetitive or irrelevant information.

![Screen Shot 2020-04-23 at 7.31.26 AM](https://solutions.narrative.io/hubfs/Screen%20Shot%202020-04-23%20at%207.31.26%20AM.png)

### Data Included in your Subscription

#### _Deduplication: idValue_

When deduplicating by ID only, you will receive a **single record for every unique ID** that satisfies the other parameters of your Buy Order. ![dedupe_ID_2](https://solutions.narrative.io/hubfs/dedupe_ID_2.jpg)

#### _Deduplication: idValue, consumedResourceURI_

When deduplicating by ID and [Uniform Resource Identifier (URI)](https://kb.narrative.io/what-is-an-uniform-resource-identifier-uri), you will receive **a single record for every unique ID<>URI pair** that satisfies the other parameters of your Order. Every App used by every ID is included. Records showing different [consumptionTypes](https://kb.narrative.io/what-are-consumption-types) are ignored.

![dedupe_ID_URI_2](https://solutions.narrative.io/hubfs/dedupe_ID_URI_2.jpg)

#### _Deduplication: idValue, consumedResourceURI, consumptionType_

When deduplicating by ID, URI _and_ [consumptionType](https://kb.narrative.io/what-are-consumption-types), you will receive **a single record for every unique combination of ID<>URI<>consumptionType** that satisfies the other parameters of your Order. Every consumptionType for every App used by every ID is included. Records showing duplicate combinations are ignored.

![dedupe_ID_URI_conType_2](https://solutions.narrative.io/hubfs/dedupe_ID_URI_conType_2.jpg)
