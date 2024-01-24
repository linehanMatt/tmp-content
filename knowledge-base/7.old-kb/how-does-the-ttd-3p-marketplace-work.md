---
title: 'How does The Trade Desk''s third-party Data Marketplace work?'
description: 'The Trade Desk''s third-party Data Marketplace allows advertisers to access and purchase data from a variety of third-party data providers'
lastUpdated: '2023-02-21T15:26:34.668Z'
tags: ['Data Egress Through Connector Apps', 'The Trade Desk']
---
The Trade Desk's third-party Data Marketplace allows advertisers to access and purchase data from a variety of third-party data providers. The data providers, such as data management platforms (DMPs), survey companies, retailers ,and other offline data providers, make their data available on the The Trade Desk's platform. Advertisers can then use this data to target their advertising efforts more effectively.

### The Trade Desk marketplace pricing

The Trade Desk pricing is expressed as “hybrid rates”: rates that represent a percentage of media cost (%) with a maximum CPM cap ($). These typically look like the following:

30% / $3.50 CPM

This means that the provider will receive 30% of the cost of the ad impression that was served when credited to this audience segment, but that if that 30% exceeds $3.50 CPM (cost per thousand impressions) then the payout will be limited to $3.50 CPM.

See _**Data rate cards**_ under **TTD Audience Taxonomies** below for more information on setting pricing in The Trade Desk.

### Syndicated audiences

Syndicated Audiences are audiences which are available to any advertiser in The Trade Desk at the same rate. Syndicated Audiences cannot have any restrictions on who can see and buy the segment; all advertisers in The Trade Desk are able to purchase the segment at the same rate. See more about how to generate syndicated audiences under **TTD Audience Taxonomies** below.

### Custom audiences

Custom Audiences are segments which are made available to specific advertisers in The Trade Desk at specific rates. Segments are only visible to advertisers which have permission to access the segment, and the rate is specific to the advertiser. See more about how to generate custom audiences under **TTD Audience Taxonomies** below.

### The Trade Desk audience taxonomies

Data in The Trade Desk's third-party Data Marketplace is modeled in a data “taxonomy”: a system of classification used to organize and segment the data that is made available on The Trade Desk by third-party data providers. This taxonomy allows advertisers to easily browse and select the data that is most relevant to their advertising efforts, as well as to search for relevant keywords in order to locate segments that are valuable for their campaign.

Technically, the The Trade Desk data taxonomy determines both which advertisers are able to access a segment and the price at which those advertisers can access the segment (through _**data rate cards**_.)

A third-party data taxonomy in The Trade Desk consists of the following components:

#### **Taxonomy elements**

Taxonomy Elements are identified via unique Taxonomy Element IDs, and their location in the hierarchical taxonomy is determined by their Parent Taxonomy Element ID.

Taxonomy Elements are either “buyable” (a segment) or “not buyable” (a container or folder level). Container levels are visible in the full path of a segment’s name when users search for the segment, but they cannot be purchased or added to a campaign (the segments under them must be purchased individually).

To learn more about The Trade Desk's data taxonomies and elements, please see [Taxonomy Design documentation](https://api.thetradedesk.com/v3/portal/data/doc/DataTaxonomyDesign) on The Trade Desk developer portal.

#### **Data rate cards**

Data rate cards, which determine which advertisers can purchase a segment and at what cost.

Data rate cards can be “system level”, in which case all advertiser accounts on The Trade Desk can access the data elements that appear under the node to which this rate card is attached. System level data rate cards and the taxonomies under them are also referred to as “Syndicated Taxonomies.”

Data rate cards can also be “custom”, meaning they are assigned with “Partner” or “Advertiser” scopes. This means that only the advertiser accounts that belong to one or other of these levels are eligible to purchase data at this price. Partners and Advertisers are identified by their Partner IDs or Advertiser IDs. In order to obtain a Partner ID or an Advertiser ID, you must reach out to the advertiser themselves. Note that the relationship between Partner and Advertiser is hierarchical (advertisers belong to a partner), so if you grant access to a partner, all advertisers under that partner will also receive access at the same price.

Data rates are inherited from container levels; all segments and containers under a specific container will receive the same price and access as the rate card attached to the container. The Trade Desk recommends designing your hierarchy to include as few rate cards as possible and to take advantage of rate card inheritance wherever possible. To learn more, read about [Taxonomy rate card inheritance](https://api.thetradedesk.com/v3/portal/data/doc/DataTaxonomyDesign#rate-inheritance) in The Trade Desk's taxonomy design documentation.

* * *

**Narrative's TTD Connector App helps you manage taxonomies with ease. To learn more about The Trade Desk Connector, see [What is the Narrative TTD Connector App?](https://kb.narrative.io/what-is-the-narrative-ttd-connector)**
