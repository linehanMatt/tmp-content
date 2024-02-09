---
title: 'How do I create a dataset in Dataset Manager?'
description: 'Bring your data into Narrative by using Dataset Manager to create a dataset, activate the dataset, and add data.'
lastUpdated: '2023-03-03T00:36:20.484Z'
tags: ['Selling Data', 'Ingesting Data']
---
### Overview

Any kind of data, in any schema, can be pushed into the Narrative Data Streaming Platform as a dataset--exactly as it is stored in your own system.

Creating a dataset defines a container that will hold your raw data. Afterwards, data can be added to your dataset container.

Follow these instructions to make your data available for use in [My Data](https://app.narrative.io/platform/my-data/datasets).

### New Dataset

- Navigate to https://app.narrative.io/platform/my-data/new-dataset

- Click "New Dataset" to create a new dataset.

#### 1\. Dataset Upload Process

Set a name and upload a sample that represents the schema and values of the future (larger) file. The sample should be less 10MBs. 

**Note:** When uploading JSON files to Narrative, please note that we accept either a single JSON object, or JSON in the popular JSON Lines format (one JSON object per line.) Read more about JSON Lines here: https://jsonlines.org/. 

#### 2\. Dataset Details

Once your dataset is ingested, you should see the new object listed at the top of your datasets at https://app.narrative.io/platform/my-data/datasets  

Below are the available metadata options for each dataset. Some metadata will have placeholders which you can update:

*   **Name**: The name of the field. _This should not contain spaces!_
*   **Description**: Provide information about the dataset. 
*   **Schema**: 
  *   Whether the field is **Required**: If this field must contain a value for a record to be added to your dataset.
  *   Whether the field is **Queryable**: If this field can be made available to buyers.
    *   Marking a field as **not queryable** will ensure that this field cannot be transmitted to other parties on the Data Collaboartion Platform. 
  *   Whether the field is **Sensitive:** Should data in this field be redacted when the data is displayed in sample UIs and APIs.  
    *   Marking a field **sensitive** will ensure that the data in this field is never shown to users within the Narrative platform unless purchased by that user and exported. To configure a field as sensitive, select the toggle on initial upload of the dataset. 
    *   Unlike **not sellable** data, data in "sensitive" fields _will_ be delivered, in the original format, when purchased.
*    **File Type**: Inferred from the sample upload.
*   **Write Mode**: This field informs how to treat new data uploaded to your dataset. Two options are supported:
    *   **append**: Use if new data should be added to your dataset.
    *   **overwrite**: Use  if new data should replace your entire dataset.

### Add Data

To add data to your dataset, you can push files to your Narrative-hosted AWS S3 bucket.

