---
title: 'Buyer Studio: Join Dataset Filter'
description: 'Use your dataset to filter for values you want to include or exclude in your subscription. '
lastUpdated: '2022-04-01T17:52:21.587Z'
tags: ['Buying Data', 'Buyer Studio']
---
New buyers looking to learn how to create a subscription in Buyer Studio should first check out [Buyer Studio: Introduction](https://kb.narrative.io/buyer-studio-introduction) 

### Overview 

The "Join Dataset" filter in Buyer Studio allows users to filter against lists they have already uploaded in Dataset Manager. The most common use case for joining a dataset is enrichment i.e. users want to take the data they already have and learn more about it by adding on additional attributes to each row of data. 

### Enrichment 

The enrichment process starts in Dataset Manager, where buyers will first infer the schema of their dataset with a sample list before pushing the full dataset to Narrative through AWS S3, the API or Dataset Manager's UI. To learn more about creating a dataset in Dataset Manger use this [link](https://kb.narrative.io/create-a-dataset).

Below is an example from a use case where Company A wants to enrich the Unique Identifiers that they already have. Company A's dataset consists of Unique Identifiers and their corresponding age, but they wanted to learn the gender of each of their unique IDs. Here is an example schema called Hubspot Contacts that represents the dataset they had before their Buyer Studio subscription:

Unique ID 1, Age:22

Unique ID 2, Age:27

Unique ID 3, Age:20

Unique ID 4, Age:20

The buyer continues the enrichment process by going into Buyer Studio, adding the Gender and Unique Identifier attributes to their order, and then continuing on to the Add Filters step. Under Unique Identifier > value they should select the Hubspot Contacts dataset under the "Join Dataset" filter. This fourth filter option is only listed under attributes that are joinable i.e. the Join Dataset filter will not show up under the Country Code attribute. 

![Screen Shot 2022-01-28 at 4.44.51 PM](https://ci5.googleusercontent.com/proxy/H3Gi3oJpT9pRDgmKBbVaIquJIbS_KYDDe2YOaC_xlXOS6zE6XQKay8wruayY4yjWSYPi5u75-lqLnBv1bGZ7MW9S32wj_fM3_lOdBGJrBVrD0R-xkxK9S9_M4a-OdT0JYzcF_Z0IKkTWAXUWCWNeVvIDakt4o-Lw7iGIGc9qASJaMJgdO_7UtAJyC0xA4KY0rITxjzYpqtj9RSnggc1IoUds7JrYA-M6DSXZirLvkjqQ8jHsWqq2mB40mEFW=s0-d-e1-ft#https://email.narrative.io/hs-fs/hubfs/Screen%20Shot%202022-01-28%20at%204.44.51%20PM.png?width=1120&upscale=true&name=Screen%20Shot%202022-01-28%20at%204.44.51%20PM.png)

Under the Gender attribute, select the "Include if Present" filter to make sure each row delivered has a unique id and a gender. The buyer finishes their order and receives a dataset with the following schema: 

Unique ID 1, Gender: male 

Unique ID 2, Gender: female

Unique ID 3, Gender: male 

Unique ID 4, Gender: female

Note that the buyer's original dataset is not included in the deliverable i.e. Age is not included in the output above. In this case ,the order's output only includes the Unique Identifier > value and Gender attributes.
