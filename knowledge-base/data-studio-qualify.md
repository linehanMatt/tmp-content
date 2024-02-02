# ---
title: 'Data Studio: Qualify'
description: 'Learn how to control the frequency certain data points show up in an output. '
lastUpdated: '2021-12-08T20:38:14.256Z'
tags: ['Buying Data', 'Buyer Studio']
---
# Introduction
Narrative Query Language (NQL) provides mechanisms for refining and deduplicating result sets. Understanding the difference between regular deduplication and using the `QUALIFY` clause with a non-unity number allows for more sophisticated data analysis and manipulation.

### Deduplication
Deduplication typically refers to removing duplicate rows from a dataset. In SQL, this is often done with the DISTINCT keyword, which eliminates redundant data, returning only unique rows.

### The QUALIFY Clause
The QUALIFY clause in NQL, when used in conjunction with window functions, provides a more granular control over which rows to filter based on specific conditions. It is especially useful when you want to retrieve more than one occurrence of a data point under specific ordering or ranking within each partition.

### Regular Deduplication vs. QUALIFY
- Regular Deduplication: Simplistically removes duplicate entries, returning a data set of unique rows.
- QUALIFY with a set number: Provides a way to select a specific occurrence of the data. For example, using QUALIFY ROW_NUMBER() = 1 returns the first entry in each partition of the data. This is similar to deduplication but provides the additional context of ranking or order.

### QUALIFY Example
Let's expand the concept of QUALIFY by selecting the first three transactions made by users, rather than just the first:

```SQL
SELECT
  "company_data"."6454"."USER_ID",
  "company_data"."6454"."TRANSACTION_AMOUNT",
  "company_data"."6454"."TRANSACTION_DATE"
FROM
  "company_data"."6454"
QUALIFY ROW_NUMBER() OVER (
    PARTITION BY "company_data"."6454"."USER_ID"
    ORDER BY "company_data"."6454"."TRANSACTION_DATE"
  ) <= 3
```
<br>

The query above:
- Partitions the data by USER_ID
- Orders the transactions within each partition by TRANSACTION_DATE
- Uses the QUALIFY clause with <= 3 to keep the first three transactions per user

# Use Cases
- Regular Deduplication: When a list of unique email addresses is needed without any consideration of their occurrence or order.
- QUALIFY: When detailed insight is required, such as the three most recent purchases per user or the top N highest-value transactions.

### Differences and When to Use Each
- Use deduplication when the presence of the data point is all that matters, irrespective of its frequency or order.
- Use QUALIFY when you want to retain a specific number of occurrences in a particular order, allowing for insights into patterns or behaviors over time.
# Conclusion
Understanding when to employ deduplication versus the QUALIFY clause in NQL queries is vital for performing accurate and insightful data analysis. The ability to specify occurrences beyond deduplication expands the analytical capabilities within the Narrative Data Collaboration Platform.