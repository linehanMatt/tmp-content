---
title: 'What is NQL?'
description: 'A brief introduction to the Narrative Query Language (NQL) and its role in transforming data collaboration on the Narrative Platform.'
lastUpdated: '2023-10-24T21:14:59.823Z'
tags: ['NQL', 'Data Collaboration', 'Rosetta Stone']
---

## What is NQL?

NQL, or Narrative Query Language, is a powerful SQL interface designed to revolutionize data experiences on the Narrative Data Collaboration Platform. By integrating seamlessly with the Rosetta Stone Attribute Catalog, NQL enables users to query, share, or purchase data across the ecosystem as efficiently as if it were all stored in a single database.

## Key Features of NQL

### Integration with Rosetta Stone Attribute Catalog

NQL stands out through its deep integration with the Rosetta Stone global attribute catalog, a central hub for normalized data attributes sourced from various companies. This integration allows users to effortlessly query data from any company on the platform that has established Access Rules, making data querying straightforward and unified.

### Simplifying Data Queries

NQL is tailored to accommodate both experienced data scientists and those new to SQL, facilitating easy derivation of insights from both personal data and the broader marketplace of datasets. It ensures that users can navigate through data silos, unlocking limitless insights without the hassle of dealing with disparate data formats.

### Permissions & Access Rules

NQL emphasizes security and governance through Access Rules, which govern table permissions based on datasets, authorized users or companies, queryable fields, costs, and any analysis restrictions. This framework ensures that queries are executed within a secure and controlled environment.

## Rosetta Stone Attributes: The Magic Behind NQL

The core of NQL's functionality lies in the Rosetta Stone Attributes, which normalize data from multiple organizations into a uniform format. This eliminates the need to manage different formats or schemas, enabling users to query data as if it were all part of their own dataset.

### Example: Querying with NQL

Consider a scenario where you need to filter data based on gender and event timestamp across multiple suppliers while managing cost:

- **Forecast Query Costs:** Use `EXPLAIN` to anticipate the query's cost.
- **Select Data:** Choose "unique_id" and "gender" attributes from the `narrative.rosetta_stone` table.
- **Filter Data:** Include only records with a gender value of 'female' and events after a specific date.
- **Cost Control:** Specify a maximum CPM for cost-effective querying.

This example illustrates how NQL facilitates complex queries through Rosetta Stone Attributes, simplifying data collaboration and analysis.

## Conclusion

NQL transforms how data is queried, shared, and analyzed within the Narrative Data Collaboration Platform. Its integration with Rosetta Stone Attributes and adherence to robust security measures through Access Rules make it an invaluable tool for anyone looking to streamline their data collaboration efforts.
