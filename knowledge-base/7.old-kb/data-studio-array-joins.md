---
title: 'Data Studio: ID Graphs'
description: 'Upload your list of Unique IDs to find ID graphs in Narrative''s system. '
lastUpdated: '2022-05-11T01:23:38.655Z'
tags: ['Buying Data', 'Data Studio']
---
## Introduction
In the realm of data collaboration and analysis, the ability to link different data sources using unique identifiers is paramount. This knowledge base article describes the process of inputting a list of unique ids to perform joins using the Narrative Query Language (NQL). An understanding of identifier relations and NQL syntax is necessary when performing data joins.

### Prerequisites
A list of unique identifiers to input for the join operation.
Basic knowledge of SQL and NQL syntax.
NQL Editor and Data Joins
In the Narrative Data Collaboration Platform, the NQL editor in the Data Studio UI allows users to input and run queries. A common task is joining datasets using unique identifiers. Here, we focus on using a list of unique identifiers to join tables/datasets with identifier relations.

## Using NQL for Joins: Main Concepts
Identifier Relation: A Rosetta Stone attribute of array type that includes unique identifiers from a dataset (e.g., a mobile_id_unique_identifier).
Join Operation: In NQL, joins can be explicit using JOIN keyword.
### Example of an NQL Join with Unique Identifiers
Here is an example of using NQL to join a company-specific dataset with Rosetta Stone data using a list of unique identifiers:

```SQL
SELECT 
  "company_data"."customer_table"."customer_id",
  "narrative"."rosetta_stone"."identifier_relation"."value" AS "mobile_id",
  "company_data"."customer_table"."purchase_amount"
FROM 
  "company_data"."customer_table"
JOIN 
  "narrative"."rosetta_stone"
ON
  "company_data"."customer_table"."customer_id" = "narrative"."rosetta_stone"."identifier_relation"
WHERE
  "narrative"."rosetta_stone"."_price_cpm_usd" <= 2.0
LIMIT 50 USD PER CALENDAR_MONTH
```


### Guidelines
- Ensure that the join condition accurately matches the corresponding fields from both the company-specific dataset and the Rosetta Stone data.
- Filter on additional constraints such as price and budget limits.

### Verification and Execution
Before execution, validate your NQL to ensure that there are no syntax errors. Use the Validate option in the NQL editor. Once the NQL passes validation, execute the query with the Run command or use EXPLAIN for an estimated data volume before creating datasets.

## Conclusion
Joining datasets using a list of unique identifiers is a critical function within the Narrative Data Collaboration Platform. Using NQL, analysts can perform these joins effectively, enabling a seamless integration of diverse data sources.