---
title: Snowflake to The Trade Desk
videoId: cf47ad5602ac1d9199d7f0e9865910fa
description: A quick video showing how to send data from Snowflake to The Trade Desk using Rosetta Stone
type: video
---
You can see here in My Data that we have a new dataset with the name that I registered in snowflake.

You can see that this dataset is hosted in Snowflake's cloud region, AWS US-east-1. And that the data utilizes a query engine of snowflake.

<!--more-->

Opening the dataset and going to the mappings tab. We see that narrative has automatically mapped my dataset to a few attributes from the Rosetta stone catalog. HL-7 gender identity, person name, hashed email, and sports team .

 Now let's query this dataset using Rosetta stone.

Opening query builder in data studio. I'm going to select. sha_256_email.Value  as an output. And I'm going to add a filter on gender and set it equal to female.  

Let's create a new dataset from the output of this query.  

Now we have a new dataset: female sports fans.

Opening to the dataset and navigating to the connections tab. I can connect this dataset to any of the connectors that I've installed in my account. Here we see the The Trade Desk connector.  Let's send this data  to our advertiser partner in the trade desk. Athena Endurance Gear.

Within minutes, my data's  delivered to The Trade Desk
