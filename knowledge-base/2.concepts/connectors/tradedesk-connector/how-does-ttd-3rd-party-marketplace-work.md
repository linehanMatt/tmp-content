---
title: 'How Does The Trade Desk’s Third-Party Data Marketplace Work?'
description: 'Exploring The Trade Desk’s third-party Data Marketplace: A guide for advertisers to access and purchase data from diverse providers.'
lastUpdated: '2024-01-31'
tags: ['Data Egress Through Connector Apps', 'The Trade Desk']
---

The Trade Desk's third-party Data Marketplace enables advertisers to access and purchase data from a variety of third-party data providers. These providers include data management platforms (DMPs), survey companies, retailers, and other offline data sources. This availability facilitates advertisers in targeting their advertising efforts more effectively.

### The Trade Desk Marketplace Pricing

The Trade Desk's pricing model is known as “hybrid rates,” which combines a percentage of media cost (%) with a maximum CPM (cost per thousand impressions) cap. An example of this would be:

- 30% / $3.50 CPM

This model means the provider receives 30% of the cost of the ad impression credited to this audience segment. However, if this percentage exceeds $3.50 CPM, the payout is capped at $3.50 CPM. For more information on setting pricing in The Trade Desk, refer to _**Data Rate Cards**_ under **TTD Audience Taxonomies**.

### Syndicated Audiences

Syndicated Audiences are available to any advertiser on The Trade Desk at the same rate and without restrictions. This means all advertisers can purchase the segment at a uniform rate. Detailed generation of syndicated audiences is discussed under **TTD Audience Taxonomies**.

### Custom Audiences

Custom Audiences are made available to specific advertisers at predetermined rates. These segments are visible only to advertisers with permission, ensuring exclusivity and tailored rates. The process for generating custom audiences is also found under **TTD Audience Taxonomies**.

### The Trade Desk Audience Taxonomies

The Trade Desk organizes its third-party data using a "taxonomy" - a classification system that segments and organizes data for easy access and selection by advertisers. This taxonomy also supports keyword searches for segment identification.

#### **Taxonomy Elements**

Taxonomy Elements, identifiable by unique IDs, are categorized within the hierarchy by their Parent Taxonomy Element ID. Elements are classified as either "buyable" (a segment) or "not buyable" (a container or folder level), with the latter being non-purchasable but visible in search paths.

For an in-depth understanding of The Trade Desk's data taxonomies and elements, visit the [Taxonomy Design documentation](https://api.thetradedesk.com/v3/portal/data/doc/DataTaxonomyDesign) on The Trade Desk developer portal.

#### **Data Rate Cards**

Data rate cards specify the purchase eligibility and cost for segments. They can be system-level, accessible to all advertisers, or custom, designated for specific partners or advertisers. The hierarchy and pricing inheritance are crucial in rate card design, ensuring efficient access and pricing distribution.

Further details on rate card inheritance can be found in the [Taxonomy Rate Card Inheritance](https://api.thetradedesk.com/v3/portal/data/doc/DataTaxonomyDesign#rate-inheritance) section of The Trade Desk's taxonomy design documentation.

---

**For assistance in managing taxonomies, the Narrative TTD Connector App offers streamlined solutions. Discover more about The Trade Desk Connector in [What is the Narrative TTD Connector App?](https://kb.narrative.io/what-is-the-narrative-ttd-connector)**
