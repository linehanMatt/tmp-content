---
title: 'What are Narrative Egress Connectors?'
description: 'Use Narrative Egress Connectors to deliver data to destinations outside of the Narrative platform'
lastUpdated: '2022-11-01T12:58:41.709Z'
tags: ['Data Egress Through Connector Apps', 'Overview']
---
### Send Data Where?

Narrative Egress connectors enable delivery of data to third party destinations outside of the  Narrative platform.  Egress connectors, developed by Narrative or third party developers, help users deliver data seamlessly to destinations such as an AWS S3 bucket, a Facebook Ads Manager account, or The TradeDesk's first party and third party Data Marketplace APIs.

### How does it work?

Users can now deliver data to their desired location without anyone at Narrative lifting a finger. The process involves no code meaning nontechnical end users can easily set up and manage their delivery preferences through the UI. Need to update the location? No problem. Users can add new destinations without Narrative's explicit approval.

#### Connector Apps

Users **must install** the respective third party Connector App in order to create the endpoint. For example, sending data directly to an S3 bucket requires installing and configuring the S3 Connector app.

1. Authorize Narrative to send data to a third party application
2. Setup "profiles" in the third party application to authenticate to the third party destination and configure company-wide settings
3. Configure "quick settings" relevant to the individual delivery subscription, such as which folder to deliver data to and the cadence on which to run new deliveries
4. Test Narrative's connection with each destination  

#### Connector Checkout Settings

Connector checkout settings **automatically become available** within My Data and Data Studio once the Connector App is correctly setup.

1. Select the profile (authorization and account information in the third party destination) for a the user's dataset or query
2. Configure delivery-specific "quick settings", such as a subdirectory within the profile's location to store the subscription, and the cadence on which data should be delivered
