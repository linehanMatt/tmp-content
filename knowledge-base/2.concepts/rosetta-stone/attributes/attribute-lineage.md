---
title: Attribute Lineage
description: Attributes are propogated from one dataset to another when possible, creating a lineage that keeps datasets connected
---

## What is Attribute Lineage?

Attribute Lineage is the process of tracking the propagation of attributes from one dataset to another. This process is essential for maintaining the semantic meaning of data across different datasets.

When a dataset is mapped to a Rosetta Stone attribute, the attribute is propagated to any dataset that is created as a derivative of the original dataset. This propagation ensures that the semantic meaning of the data is preserved as it moves through the data pipeline

## Why is Attribute Lineage Important?

Attribute Lineage is important because it allows you to maintain the semantic meaning of data as it moves through the data pipeline. This is essential for ensuring that the data remains accurate and meaningful as it is used for analysis and decision-making.

Rosetta Stone Attributes are the core of the normalization engine of Narrative's Data Collaboration Platform and keeping them consistent and populated across as much data as possible enables the seamless flow of data between different datasets and organizations.

## How Does Attribute Lineage Work?

Attribute Lineage works by tracking the propagation of attributes from one dataset to another. When a dataset is mapped to a Rosetta Stone attribute, the attribute is propagated to any dataset that is created as a derivative of the original dataset. This propagation ensures that the semantic meaning of the data is preserved as it moves through the data pipeline

### Example: Attribute Lineage in Action

We'll use a simple NQL query to illustrate the different ways that attributes can be propagated from one dataset to another.

#### From Global Rosetta Stone Queries

```sql
SELECT
  narrative.rosetta_stone.event_timestamp,
FROM
    narrative.rosetta_stone
```

In this query, the `event_timestamp` attribute is propagated from the `narrative.rosetta_stone` dataset -- which itself is mapping from a non-rosetta stone dataset -- to the result of the query. This propagation ensures that the semantic meaning of the `event_timestamp` attribute is preserved as it moves through the data pipeline.

#### From Company Specific Rosetta Stone Queries

A company can query their own data using rosetta stone attributes as well.  The lineage works the same way as with global rosetta stone queries.

```sql
SELECT
  company_data._rosetta_stone.event_timestamp,
FROM
    company_data._rosetta_stone
```

#### From Non-Rosetta Stone Queries

```sql
SELECT
  company_data.company_table.event_timestamp
FROM
    company_data.company_table
```

Even though this query does not use Rosetta Stone directly as long as the `event_timestamp` column in `company_table` is mapped to a Rosetta Stone attribute, the lineage will be preserved in the resulting dataset.

### When Lineage is Not Preserved

There are a few scenarios where lineage is not preserved:

- When a dataset is not mapped to a Rosetta Stone attribute.  In this case there is no lineage to preserve
- When a dataset is mapped to a Rosetta Stone attribute but the attribute is not used in the query.  In this case the lineage is not preserved in the result of the query.
- When a field is selected that could have preserved the lineage, but the field is transformed in a way that breaks the lineage.  For example, if a date field is truncated, the lineage is broken because the resulting output no longer has the same semantic meaning as the original field.
- If a attribute mapping does not exist at the time the derivitive dataset is created, and later that mapping is added, the lineage will not be preserved in the derivitive dataset unless it is recreated.

## Conclusion

Attribute Lineage is an essential part of maintaining the semantic meaning of data as it moves through the data pipeline. By tracking the propagation of attributes from one dataset to another, you can ensure that the data remains accurate and meaningful as it is used for analysis and decision-making. This is essential for ensuring that the data remains accurate and meaningful as it is used for analysis and decision-making. Rosetta Stone Attributes are the core of the normalization engine of Narrative's Data Collaboration Platform and keeping them consistent and populated across as much data as possible enables the seamless flow of data between different datasets and organizations.
