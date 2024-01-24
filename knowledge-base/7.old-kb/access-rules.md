---
title: 'What is an access rule?'
description: 'Access rules let data providers control who can purchase their data and the terms of purchase.'
lastUpdated: '2023-04-24T23:05:19.054Z'
tags: ['Selling Data', 'Seller Studio']
---
### Overview

After [creating a dataset](https://kb.narrative.io/create-a-dataset), providers use access rules to make data available for purchase in custom subscriptions.

An **access rule** is a set of business rules defining what records from a dataset are available for purchase, the commercial terms of the purchase, and who is eligible to make a purchase.

Use access rules to:

*   Control which records from a dataset can be purchased
*   Set different price rates for different records from a dataset
*   Set different rates for different buyers
*   Make your data available only to specific buyers

A dataset with no access rules cannot be purchased in custom subscriptions.

### Access Rule Components

#### Description

Set a descriptive name to identify each access rule.

#### Price

Set a price for every 1000 records of raw data.

If it is possible for a record to be purchased under more than one access rule, the highest-priced access rule will apply.

#### Constraints

Set logic to control which records from a dataset can be acquired under the terms of an access rule and which cannot.

Create an access rule without data constraints to make all of your data available in the same access rule.

#### Buyers

Decide to whom each access rule applies.

Maintain tighter control by setting either an **inclusion list** of companies that an access rule applies to or an **exclusion list** of companies that an access rule does not apply to, or leave an access rule unconstrained to apply universally to all buyer companies.

### Access Rule Logic

When a buyer places a subscription, their data is pulled from datasets with access rules open to the buyer.

Given a record from a dataset that matches the buyer's specifications, the record will be sold according to the first compatible access rule.

Access rules apply from highest-priced first to lowest-priced last.

### Access Rule Example Use Cases

#### Price records at different rates

Set granular logic to determine the price at which each record of data can be purchased.

For example, using an adapted [nominal tuna catch dataset from the Indian Ocean Tuna Commission](https://www.iotc.org/data/datasets) (sample below), a seller could price records with a **Fishery\_Type** of "Industrial Fishing" at a different rate than records where the **Fishery\_Type** column contains "Artisanal Fishing."

Fleet\_Code,IOTC\_Fishing\_Zone,Year,Fishery\_Type,Gear,Species,Species\_Latin,Species\_Group,Species\_is\_IOTC,Catch  
ARE,Western Indian Ocean,1950,Artisanal Fishing,Gillnet,Narrow-barred Spanish mackerel,Scomberomorus commerson,SEERFISH,TRUE,603  
ARE,Western Indian Ocean,1950,Artisanal Fishing,Troll line,Longtail tuna,Thunnus tonggol,TUNAS,TRUE,83  
AUS,Eastern Indian Ocean,1950,Artisanal Fishing,Unclassified,Seerfishes nei,Scomberomorus spp.,SEERFISH,TRUE,100  
CHN,Western Indian Ocean,2015,Industrial Fishing,Longline,Other non tuna-like fishes nei,Fishes non Scombroidei,OTHERS,FALSE,52  
COM,Western Indian Ocean,1950,Artisanal Fishing,Gillnet,"Non targeted, associated and dependent species",n/a,OTHERS,FALSE,10  
EUREU,Western Indian Ocean,1950,Artisanal Fishing,Hand line and Troll line,Yellowfin tuna,Thunnus albacares,TUNAS,TRUE,79  
IDN,Eastern Indian Ocean,1950,Artisanal Fishing,Beach seine,Narrow-barred Spanish mackerel,Scomberomorus commerson,SEERFISH,TRUE,6  
TWN,Eastern Indian Ocean,2019,Industrial Fishing,Longline Fresh,Hammerhead sharks nei,Sphyrna spp.,SHARKS,FALSE,0  
TZA,Western Indian Ocean,2019,Industrial Fishing,Longline,Yellowfin tuna,Thunnus albacares,TUNAS,TRUE,1  
ZAF,Western Indian Ocean,2019,Industrial Fishing,Longline targeting swordfish,Yellowfin tuna,Thunnus albacares,TUNAS,TRUE,389
