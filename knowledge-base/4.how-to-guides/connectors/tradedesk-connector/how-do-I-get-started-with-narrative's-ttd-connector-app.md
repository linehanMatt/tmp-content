---
title: 'How do I get started with Narrative''s TTD Connector App?'
description: 'Determine whether you need to push data via the First Party or Third Party endpoints, select your data, and push!'
lastUpdated: '2023-02-07T19:54:55.217Z'
tags: ['Data Egress Through Connector Apps', 'The Trade Desk']
---
Getting started with Narrative’s TTD Connector Apps is straightforward. You can push data from any dataset or data stream in your account (or you can acquire data from third parties and push the resulting dataset).

First, determine the use case for your data and whether it should be shared with TTD via the first party (TTD 1P Connector App) or third party (TTD 3P Connector App) routes:

### Third Party vs First Party Data in TTD

Simply put, TTD considers any data that is licensed off of their platform to be “first party” and any data that is being licensed within TTD’s platform via their marketplace to be “third party.” If you are uncertain which use case you need, read more on What is the difference between 1P and 3P data in TTD?

### TTD 3P Connector App

If you are interested in pushing third party data to TTD, you will want to utilize the TTD 3P Connector App.

#### Step 1: Install the Narrative 3P Connector App

Install the Narrative 3P Connector App and provide your TTD Brand ID (which can be obtained from your TTD account representative.)

![](https://solutions.narrative.io/hubfs/image-png.png)

#### Step 2: Create your taxonomy

Generate your initial TTD Taxonomy by clicking “download” in the “Taxonomy Management” section, editing and re-uploading the provided CSV template. For tips on crafting your taxonomy and gaining TTD approval, see TTD 3P Taxonomies below.

Narrative’s taxonomy management visualization will help you validate your taxonomy design. Your TTD rep will ensure that your taxonomy follows all taxonomy design and pricing best practices. Note: be sure to get approval of your taxonomy from your Narrative Account Rep and your TradeDesk Account Rep prior to pushing “synchronize”. 

![](https://solutions.narrative.io/hubfs/image-png-1.png)

#### **Step 3: Select your data and merchandize it** 

Use Narrative’s Dataset Manager to upload your raw data, and Seller Studio to slice, dice and merchandize your dataset into Data Stream products representing audiences that can be pushed to TTD. You will need to include one of TTD’s supported attributes as a “deliverable” field. (see What type of data does TTD Connector Accept?) Be sure to add a price, name and meaningful description for your audiences! 

![](https://solutions.narrative.io/hubfs/image-png-2.png)

#### Step 4: Push to TTD

Data is pushed to TTD as soon as you click “Save”, but must be processed within their platform:

*   Taxonomy elements pushed to TTD are typically automatically approved within TTD’s platform and made available to buyers within 48 hours.
*   The initial push for a large taxonomy may sometimes take up to a week to become available within TTD.
*   User data that is pushed to TTD and associated with a Taxonomy element is available within the hour, as long as the Data Taxonomy element has been approved.

### Taxonomy Management

You will see the following fields in the "Taxonomy Management" screen:

**Field**

**Description**

Name

Display name of segment in The Trade Desk

Description

Description of segment to be displayed in The Trade Desk

Element ID 

Unique ID that identifies this segment in The Trade Desk

Parent Element ID

Unique ID of the parent element

Rate Card

The rate card determines what price this segment is available at, as well as which partners or advertisers have access to this segment in The Trade Desk

Price

Price at which this segment is offered in The Trade Desk's marketplace. Prices appear in the following format:

*   **Revenue Share**: % of media to be charged to the buyer and payable to the segment provider
*   **CPM Cap:** $ CPM value at which payout to the provider is capped

Received IDs

The number of unique IDs that have been sent to The Trade Desk for this segment.

Active IDs

The number of device IDs that The Trade Desk was able to match to an ID for this segment.

Sync Status

The sync status of this segment.

Full Path

The full path that a buyer will see when viewing this segment in The Trade Desk.

Buyable

Buyable segments contain users and can be purchased, non-buyable elements are containers or folders for constructing the taxonomy hierarchy only. 

Data Stream ID

Data Stream to be used as the source of data for this segment. You can add or update a Data Stream for this segment at any time (but any data that has already been sent to The Trade Desk will not be updated.) 

