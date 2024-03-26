---
title: 'S3 Connector App and Checkout Settings'
description: 'A step-by-step guide on configuring the S3 Connector App for direct data deliveries to your AWS S3 bucket.'
lastUpdated: '2024-01-31'
tags: ['Data Egress Through Connector Apps', 'Overview']
---

For an introduction to Outbound Connectors, see: [What are Narrative Outbound Connectors](https://kb.narrative.io/what-is-a-narrative-outbound-connector).

### Setting Up the AWS S3 Connector App

#### **Prerequisites**

- Ensure you have an AWS account. Create one [here](https://aws.amazon.com/pm/serv-s3/?trk=fecf68c9-3874-4ae2-a7ed-72b6d19c8034&sc_channel=ps&sc_campaign=acquisition&sc_medium=ACQ-P|PS-GO|Brand|Desktop|SU|Storage|S3|US|EN|Text&s_kwcid=AL!4422!3!488982706710!p!!g!!amazon%20s3%20account&ef_id=Cj0KCQjw4PKTBhD8ARIsAHChzRLobwTN-0URXY5Rt3vl4UpP2B0_uCA92enmL1SxIZX6Ff-s9rLmJvYaArGpEALw_wcB:G:s&s_kwcid=AL!4422!3!488982706710!p!!g!!amazon%20s3%20account) if needed.

#### **Installing the S3 Connector**

1. Access the S3 Connector App via the [apps tab](https://app.narrative.io/apps) in Narrative's platform.
2. Click the install button on the app's tile. Contact <support@narrative.io> for installation issues.

#### **Configuring Bucket Profiles**

1. **Launch the App:** Open the S3 Connector App and select "Connector Settings".
2. **Create a New Profile:** Click "+ New Profile", then enter your profile name, description, and AWS S3 bucket name.
   - **Profile Name:** Use a descriptive name, such as "North American Location Data".
   - **Description:** Detail the use case for easier internal recognition.
   - **Bucket Name:** The exact name of your S3 bucket (e.g., "narrative-testing-bucket").

#### **Granting Narrative Access**

1. **Bucket Policy:** Add the provided policy to your S3 bucket via the AWS console under the Permissions tab.
2. **Bucket Tag:** Add the provided Tag Key and Value to your bucket for verification.

#### **Finalizing Setup**

1. **Test Connection:** Ensure the setup is correct by testing the connection in the S3 Connector App.
2. **File Configuration:** Choose your preferred file type (CSV, TSV, JSON, or Parquet) and configure as necessary for CSV and TSV.

Click "Save And Finish" to complete the setup.

### Using Your S3 Destination During Checkout

1. **Select S3 Connector:** During checkout in Buyer Studio or Data Marketplace, activate the S3 connector and choose your profile.
2. **Subdirectory Organization:** Optionally, specify a subdirectory for better organization of data deliveries.
3. **Multiple Profiles:** To send data to multiple buckets, select "Add An Additional Profile" and configure each as needed.

Confirm the settings and complete the checkout process to start receiving data in your specified S3 bucket. Contact <support@narrative.io> for further assistance.

### Advanced Settings

The S3 Connector offers advanced settings that can be configured exclusively through the API. These settings provide more control over how data is processed and delivered to your AWS S3 bucket. One notable setting is the `remove_metadata` flag, which allows for more refined data management.

#### **API-Only Configuration Options**

Below is an example of advanced settings available through the API:

```json
{
  "bucket_prefix": "Delivery_dataset_for_Fanatics_Data_Delivery_to_CadentTV_Real",
  "historical_data_enabled": true,
  "remove_metadata": true
}
```

#### Understanding the remove_metadata Flag
Functionality: When set to true, the `remove_metadata` option instructs the S3 Connector to remove all fields beginning with _nio from the delivered data. This is particularly useful for users looking to streamline their datasets by excluding metadata that may not be relevant to their analysis or storage needs.

#### Behavior with Different File Types:

- CSV Files: Regardless of the `remove_metadata` setting, all materialized fields are always removed to ensure a cleaner dataset. If remove_metadata is set to true, `_nio.*` fields are also excluded from the final dataset.

- JSON and Parquet Files: If `remove_metadata` is set to true, both materialized fields and `_nio.*` fields are removed. This ensures that the delivered data is free of unnecessary metadata, optimizing storage and simplifying data processing.

This advanced functionality provides users with greater flexibility and control over their data deliveries, allowing for customization to meet specific needs or preferences. 

For further assistance or to enable these advanced settings, please contact support@narrative.io.
