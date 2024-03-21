---
title: Best Practices for Delivering Audience Data to Connectors
description: Guidelines on preparing and delivering audience data to Narrative and Connector destinations like The Trade Desk, Google or Facebook.
lastUpdated: '2024-03-21T23:05:19.054Z'
tags:
  - data-preparation
  - audience-delivery
  - narrative-connectors
---

There are a few best practice recommendations and requirements to be aware of when delivering audience data to [Connector](../connectors) destinations such as The Trade Desk, Google or Facebook. This guide outlines essential steps and strategies for structuring and delivering your data effectively.

## Data Preparation

Before sending data to a Connector that accepts audience data, ensure your data includes attributes mapped to the appropriate Rosetta Stone attribute as required by that destination. Required attributes vary by destination. For instance, when delivering data to the Google Display & Video 360 Connector, your data should include at least one of the following sets of information:

- SHA256 hashed email
- SHA256 hashed phone number
- SHA256 hashed first name, SHA256 hashed last name, zip code and country code

If your data lacks these identifiers but you wish to deliver it as an audience, contact your Narrative account representative for assistance.

Refer to the specific Connector Destination [documentation](../connectors) in our knowledge base for a detailed list of supported attributes. 

## Creating Datasets to Represent Audiences

In order to deliver data to a Connector, you will structure your data in one or more datasets that represent those audiences.

Here are a few common strategies for structuring your datasets:

### Strategy 1: Dataset Per Audience

In this approach, you create a separate dataset for each audience. This method simplifies the process of delivering targeted data. The dataset's name and description should correspond directly to the audience it represents.

- **Dataset name**: `audience_name`
- **Dataset description**: `audience_description`

Example table structure:

| sha256_hashed_email |
|---------------------|
| abcd                |
| abcd2               |
| abcd3               |

**Best used for**: 
  - Creating and managing audience data independently prior to delivery to Narrative.
  - Situations where API integration facilitates straightforward dataset creation for new audiences.
  - When datasets are created once and updated with new identifiers as needed.

### Strategy 2: Master Dataset Containing All Audiences

This method involves a single, comprehensive dataset that includes all audience data. Each audience is identified by a unique ID and a display name, streamlining the management and update process.

- **Dataset name**: `master_audiences_dataset`
- **Dataset description**: `Contains all audience datasets, each distinguished by a unique identifier and display name.`

Example table structure:

| sha256_hashed_email | audience_unique_id | audience_display_name |
|---------------------|--------------------|-----------------------|
| abcd                | 1234               | audience_name_1       |
| abcd2               | 4567               | audience_name_2       |
| abcd3               | 7891               | audience_name_3       |

**Best used for**: 
  - Centralizing management of multiple audiences within a single dataset.
  - Simplifying dataset updates by appending new data rows for any audience (including new audiences) to the existing dataset.

### Strategy 3: Master Dataset Containing Raw Data for Audience Refinement

Deliver a master dataset filled with raw data to craft specific audiences using Narrative's tools. This strategy prioritizes minimal preprocessing and leverages the platform's capabilities for data normalization and audience segmentation and querying.

- **Dataset name**: `master_dataset`
- **Dataset description**: `Contains raw data poised for segmentation into refined audiences.`

Example table structure:

| sha256_hashed_email | age | gender | estimated_household_income |
|---------------------|-----|--------|----------------------------|
| abcd                | 34  | male   | $32,000                    |
| abcd2               | 74  | female | $85,000                    |
| abcd3               | 32  | female | $52,000                    |

In this example, you can use [Data Studio](/knowledge-base/how-to-guides/data-studio) or [NQL](/knowledge-base/how-to-guides/data-studio/nql-editor-how-to) to craft audiences such as "females earning $50k+" or "30-45 year olds" from the underlying data and deliver only the identifiers that match those queries. 

**Best used for**: 
  - Sending data to Narrative with minimal preprocessing.
  - Employing a single dataset strategy while utilizing Narrative's normalization and querying tools for audience creation.


## Normalizing Data

Normalize your dataset to prepare it for delivery. Map deliverable fields (e.g., SHA256 hashed email) to the correct attributes with Narrative's Rosetta Stone mapping automation.

## Adding a Connector

After normalizing data in your dataset, you are ready to deliver it to a Connector. Learn more about connectors [here](../connectors).
