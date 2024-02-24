---
title: 'How to Install "Narrative Data Collaboration powered by Rosetta Stone" in Snowflake Marketplace'
description: 'Step-by-step guide on installing and configuring the Narrative Data Collaboration app in Snowflake for advanced data collaboration and integration functionalities.'
lastUpdated: '2023-04-24T23:05:19.054Z'
tags: ['installation', 'snowflake', 'narrative-data-collaboration', 'rosetta-stone', 'marketplace']
---

## Introduction

This knowledge base (KB) article guides you through the process of installing the **"Narrative Data Collaboration powered by Rosetta Stone"** application from the Snowflake Marketplace. This app enables powerful data collaboration and integration capabilities within your Snowflake environment.

### Prerequisites

- You must be an ACCOUNTADMIN or have equivalent privileges in your Snowflake account to complete this installation.

> **Note:** If you encounter any issues during the installation process, please refer to the Narrative Knowledge Base article or contact our support team at support@narrative.io.

## Installation Steps

### Step 1: Setup External Access Integration

To allow the Narrative Data Collaboration app to access the Narrative Platform API from Snowflake, you must create an External Access Integration. This step enables a Snowflake Network Rule for accessing `api.narrative.io`.

1. Open a new Snowflake Worksheet within the same warehouse intended for the app.
2. Execute the necessary SQL statements to create the External Access Integration. These statements must be run individually by highlighting each and clicking **"RUN."**

> **Note:** Failing to complete this step properly may result in an error. For a smoother experience, ensure this step is correctly executed.

### Step 2: Setup Narrative API Token

The app requires an API token for accessing the Narrative Platform API.

1. Sign up or log in at Narrative Platform.
2. Follow the guide to **"Create a Long-Lived Access Token"**.
3. Ensure your API token has the following permissions:
   - Data Planes: Read and Write
   - Datasets: Read and Write
   - Jobs: Read and Write

### Step 3: Setup Compute Warehouse

Choose a Snowflake warehouse to run app actions, such as executing queries and delivering data to connectors like The TradeDesk.

- It's recommended to use a Snowpark-optimized Warehouse for optimal performance.

### Step 4: Grant Privileges

The app needs the `EXECUTE TASK` privilege to run background jobs for data querying and delivery on a schedule.

### Step 5: Setup Target Table

Select a Snowflake table to serve as the target for your queries. This table will be registered as a Dataset on the Narrative Platform, and queries will be executed against it within your Snowflake account.

### Step 6: Upload Sample (Optional)

Optionally, upload a sample of your source table to Narrative for automatic field standardization using Rosetta Stone. This step is necessary for many use cases, including data delivery to connectors like The TradeDesk or Facebook.

- If you opt not to upload a sample, contact Narrative Support for assistance in preparing your source table.

### Step 7: Setup API Polling

Configure how often the Narrative Data Collaboration app should poll the Narrative API for new tasks. While the default setting is once per hour, you may customize this frequency with a crontab expression. Here are a few default polling frequencies you might want to use:

- **Every 5 minutes:** `*/5 * * * *`
- **Every hour:** `0 * * * *`

> **Note:** Disabling polling will stop the application from querying data or delivering it to your endpoints as scheduled.

By following these steps, you'll successfully install and configure the **"Narrative Data Collaboration powered by Rosetta Stone"** application within your Snowflake environment, enabling advanced data collaboration and integration functionalities.
