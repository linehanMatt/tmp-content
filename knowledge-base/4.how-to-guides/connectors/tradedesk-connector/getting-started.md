---
title: 'How do I get started with The Trade Desk Connector?'
description: 'Getting started only takes a couple of steps and can happen in minutes'
lastUpdated: '2023-02-07T19:54:55.217Z'
tags: ['Data Egress Through Connector Apps', 'The Trade Desk']
---
Getting started with Narrative’s TTD Connector Apps is straightforward. You can push data from any dataset or data stream in your account \(or you can acquire data from third parties and push the resulting dataset\).

First, determine the use case for your data and whether it should be shared with TTD via the first party \(TTD 1P Connector App) or third party \(TTD 3P Connector App\) routes:

### Third Party vs First Party Data in TTD

Simply put, TTD considers any data that is owned by the advertiser or licensed and shared with an advertiser outside of TTD to be “first party”, and any data that is being sold within TTD’s marketplace to be “third party.” Read on for more details on both types.

### TTD 1P Data

If you want to share your own data with your own advertiser account on The Trade Desk or with another advertiser that has given you their Advertiser ID and Secret Key, you are looking to push first party data to The Trade Desk.  Read more at [How to Share Your Data with an Advertiser Using The Trade Desk Connector (1P)](/knowledge-base/how-to-guides/connectors/tradedesk-connector/ttd-1p-data).


### TTD 3P Data

If you are interested in pushing third party data to TTD, you will want to utilize the TTD 3P Connector App. Read more below to learn about pushing 3P Data.

#### Install the Narrative TTD Connector App

Install the Narrative TTD Connector App and provide your The Trade Desk Brand ID \(which can be obtained from your TTD account representative.\)

All users will need a TTD Brand ID in order to deliver data to the Trade Desk marketplace.  IF you do not have one, reach out to your Narrative relationship manager who can help facilitate getting a new Brand ID using Narrative's connection with The Trade Desk. 

![Install the Narrative 3P Connector](https://solutions.narrative.io/hubfs/image-png.png)

#### Create your taxonomy

Generate your initial TTD Taxonomy by clicking “download” in the “Taxonomy Management” section, editing and re-uploading the provided CSV template. For tips on crafting your taxonomy and gaining TTD approval, see TTD 3P Taxonomies below.

Narrative’s taxonomy management visualization will help you validate your taxonomy design. Your TTD rep will ensure that your taxonomy follows all taxonomy design and pricing best practices. Note: be sure to get approval of your taxonomy from your Narrative Account Rep and your TradeDesk Account Rep prior to pushing “synchronize”.

![Create your taxonomy](https://solutions.narrative.io/hubfs/image-png-1.png)

#### Select your data and merchandize it

Use Narrative’s Dataset Manager to upload your raw data, and Seller Studio to slice, dice and merchandize your dataset into Data Stream products representing audiences that can be pushed to TTD. You will need to include one of TTD’s supported attributes as a “deliverable” field. \(see What type of data does TTD Connector Accept?\) Be sure to add a price, name and meaningful description for your audiences!

![Select your data](https://solutions.narrative.io/hubfs/image-png-2.png)

#### Push to TTD

Data is pushed to TTD as soon as you click “Save”, but must be processed within their platform:

* Taxonomy elements pushed to TTD are typically automatically approved within TTD’s platform and made available to buyers within 48 hours.
* The initial push for a large taxonomy may sometimes take up to a week to become available within TTD.
* User data that is pushed to TTD and associated with a Taxonomy element is available within the hour, as long as the Data Taxonomy element has been approved.

### Taxonomy Management

You will see the following fields in the "Taxonomy Management" screen:

| Field              | Description                                                                                                                                                  |
|--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Name               | Display name of segment in The Trade Desk                                                                                                                    |
| Description        | Description of segment to be displayed in The Trade Desk                                                                                                     |
| Element ID         | Unique ID that identifies this segment in The Trade Desk                                                                                                     |
| Parent Element ID  | Unique ID of the parent element                                                                                                                              |
| Rate Card          | The rate card determines what price this segment is available at, as well as which partners or advertisers have access to this segment in The Trade Desk     |
| Price              | Price at which this segment is offered in The Trade Desk's marketplace. Prices appear in the following format: Revenue Share, CPM Cap                        |
| Received IDs       | The number of unique IDs that have been sent to The Trade Desk for this segment.                                                                             |
| Active IDs         | The number of device IDs that The Trade Desk was able to match to an ID for this segment.                                                                    |
| Sync Status        | The sync status of this segment.                                                                                                                             |
| Full Path          | The full path that a buyer will see when viewing this segment in The Trade Desk.                                                                             |
| Buyable            | Buyable segments contain users and can be purchased, non-buyable elements are containers or folders for constructing the taxonomy hierarchy only.            |
| Data Stream ID     | Data Stream to be used as the source of data for this segment. You can add or update a Data Stream for this segment at any time.                             |
