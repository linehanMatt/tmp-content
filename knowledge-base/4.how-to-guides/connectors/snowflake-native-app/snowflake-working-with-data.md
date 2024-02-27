---
title: 'Working with Datasets Hosted in the Snowflake Data Plane'
description: 'A guide to managing and querying datasets within the Snowflake Data Plane through the Narrative platform.'
lastUpdated: '2023-04-24T23:05:19.054Z'
tags: ['Snowflake', 'Data Plane', 'Datasets', 'Narrative', 'Data Collaboration']
---

# Working with Datasets Hosted in the Snowflake Data Plane

Narrative's Data Collaboration Platform offers seamless integration with Snowflake, enabling customers to host and manage their datasets directly within their Snowflake Data Plane. This integration ensures that datasets hosted on Snowflake are fully accessible and manageable through the Narrative Control Plane, providing a unified user interface (UI) for comprehensive data collaboration. This article outlines the workflow and benefits of working with datasets hosted in the Snowflake Data Plane.

For more information about the Narrative concepts of Control Plane and Data Plane, please refer to the following knowledge-base articles:

- [What is a control plane](/knowledge-base/concepts/key-narrative-concepts/what-is-a-control-plane)
- [What is a data plane](/knowledge-base/concepts/key-narrative-concepts/what-is-a-data-plane)

## Accessing Snowflake Hosted Datasets

Datasets that are hosted in the customer's Snowflake Data Plane are readily available from "My Data" in the Narrative Control Plane (UI). This integration ensures a seamless experience for users, enabling them to access and manage their Snowflake datasets directly from within the Narrative platform.

## Query Execution and Data Management

### Query Builder and Narrative Query Language (NQL)

- Dataset queries generated in the Query Builder or elsewhere on the Narrative platform are executed directly within the customer's Snowflake account. This ensures that data remains secure and under the customer's control.
- Queries built in Narrative Query Language (NQL) are compiled to Snowflake SQL and run in the customer's Snowflake account, allowing for precise and flexible data manipulation.

### Query Output

- The output of a query is stored in the Narrative Data Collaboration (Snowflake Native App)'s database within the customer's Snowflake account. This enables the direct use and analysis of query results within the Snowflake ecosystem.
- Additionally, the output of the query is registered as a new dataset in the Narrative Control Plane, facilitating further collaboration and data sharing.

## Sample Data and Statistics

Datasets in Snowflake calculate and send Sample Data and Statistics to the Narrative Control Plane. These elements are crucial for:
- **Rosetta Stone's ML Model (Sample Data)**: Helps in mapping the data, enhancing the accuracy and efficiency of data collaboration.
- **Rosetta AI (Statistics)**: Provides vital insights for data mapping and understanding, enabling the Narrative platform to automatically generate datasets and facilitate their use in the connector framework.

These features are particularly important for enabling automated dataset generation and integration with platforms such as The Trade Desk.

## Working with Narrative Connectors 

Any dataset hosted in Snowflake can be seamlessly connected to the Narrative Connector Framework. This connection enables datasets to be utilized across a wide range of applications and services, enhancing the flexibility and utility of data managed through the Narrative platform.

For more information on leveraging your Snowflake datasets in collaboration efforts and connecting them to platforms like The Trade Desk, refer to our articles on connector destinations:

- [Sending Data to The Trade Desk](/knowledge-base/how-to-guides/connectors/tradedesk-connector).
- [Sending Data to Facebook](/knowledge-base/how-to-guides/connectors/facebook-connector)

