---
title: 'Narrative Query Language (NQL): Overview'
description: 'Explore the capabilities of Narrative Query Language (NQL) for querying datasets, forecasting data availability, and enhancing data collaboration on the Narrative Platform.'
lastUpdated: '2023-12-28T15:57:21.944Z'
tags: ['NQL', 'Welcome Guide']
---

### Quickstart Guide to NQL

NQL empowers users to perform complex queries on datasets within the Narrative Data Collaboration Platform. Here's how to begin:

- **Basic Query Example:** Find rows where gender equals 'female' and event timestamp is after October 1, 2023, with a cost-per-mille (CPM) of up to $2.00:

    ```sql
    EXPLAIN  
    SELECT  
      narrative.rosetta_stone."unique_id"."value",  
      narrative.rosetta_stone."hl7_gender"."gender"  
    FROM  
      narrative.rosetta_stone  
    WHERE  
      narrative.rosetta_stone."hl7_gender"."gender" = 'female'  
      AND narrative.rosetta_stone."event_timestamp" > '2023-10-01'  
      AND narrative.rosetta_stone._price_cpm_usd <= 2.0;
    ```

### NQL Query Editor in Data Studio UI

The NQL Query Editor, integrated within the Data Studio UI, allows for straightforward query construction and execution. Access the editor [here](https://app.narrative.io/platform/data-studio).

### Understanding Datasets and Access Rules

- **Datasets:** NQL operates on datasets within the `company_data` namespace or the global `narrative.rosetta_stone` namespace. Ensure datasets are accessible via Access Rules for querying. [Learn more about Datasets](https://kb.narrative.io/how-narrative-works-introduction).
- **Access Rules:** Define who can query a dataset, at what price, and under what conditions. [Learn more about Access Rules](https://kb.narrative.io/how-narrative-works-introduction).

### Utilizing Rosetta Stone Attributes

Narrative's global data attribute catalog, Rosetta Stone, standardizes data attributes for efficient querying. Use the `narrative.rosetta_stone` namespace to reference these attributes in your queries. Attributes can be complex objects requiring direct reference to child properties.

### Query Features and Cost Control

NQL offers features for controlling query costs and forecasting data and costs:

- **Cost Control:** Limit query costs by specifying a maximum CPM (`_price_cpm_usd`) or setting a budget (`LIMIT`).
- **Forecasting:** Use `EXPLAIN` before your query to forecast data amounts and associated costs.
- **Materialized Views:** Create materialized views to cache query results as new datasets within the platform, using `CREATE MATERIALIZED VIEW`.

### Access Rules and Direct Querying

Directly query datasets using internal or external access rules by referencing the access rule's name within your query syntax.

### Embedded Namespaces and Reserved Fields

NQL supports querying Rosetta Stone attributes directly through the `_rosetta_stone` embedded namespace. Use reserved fields like `_price_cpm_usd` for price filtering.

### API Services for NQL

Access NQL functionality programmatically via API endpoints for running, parsing, and compiling NQL queries. Check our [API Documentation](https://api.narrative.dev/) for detailed information.

### Additional Resources

- [How Narrative Works](/knowledge-base/getting-started/how-narrative-works): A foundational guide to the Narrative platform's workings.

This overview provides the essential information to get started with NQL, enabling efficient data querying and management on the Narrative Platform.
