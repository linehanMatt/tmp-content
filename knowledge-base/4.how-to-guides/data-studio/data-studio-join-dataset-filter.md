---
title: 'Buyer Studio: Join Dataset Filter'
description: 'Use your dataset to filter for values you want to include or exclude in your subscription. '
lastUpdated: '2022-04-01T17:52:21.587Z'
tags: ['Buying Data', 'Buyer Studio']
---

## Data Studio's NQL Join Filter

As you delve into the realm of data analysis and collaboration using [Narrative's Data Collaboration Platform](https://app.narrative.io/platform/data-studio), mastering the Narrative Query Language (NQL) join filter is an essential skill. This capability enables a seamless fusion of diverse datasets, paving the way for more comprehensive insights and an enriched analytical experience.

### The Essence of Join Operations

The join operation is a pillar of relational database systems, and in NQL, it plays a critical role in merging data from different sources. By specifying a join condition, NQL aligns rows from two datasets based on a common attribute or relation, allowing you to analyze interrelated data with finesse.

### Utilizing NQL's Join Filter in Data Studio

To initiate a join filter operation in Data Studio, follow these steps:

1. **Select Your Datasets:** Begin by choosing your primary dataset and the dataset(s) you wish to join. Data Studio provides an intuitive user interface enabling easy selection and management of these datasets.

2. **Specify Your Join Type:** NQL supports various join types including INNER JOIN, LEFT JOIN, RIGHT JOIN, and FULL JOIN. Select the appropriate join type based on your analytical requirements.

3. **Define the Join Condition:** Clearly define the join condition by using fully qualified column names. This condition determines how rows from the combined datasets will correlate with one another.

4. **Projection of Columns:** After the join, select the columns you wish to retain in the final output. This projection of columns ensures that you only carry forward the data essential for your analysis.

5. **Execute and Analyze:** With everything set, execute your NQL query. Data Studio processes your join filter and returns the merged dataset, which you can then proceed to analyze or visualize as needed.

### Real-World Example of NQL Join Filter

Suppose we have two datasets: `sales_data` containing sales transactions and `product_catalog` containing product details. To analyze sales figures against product types, we'd perform a join as follows:

```nql
SELECT
  sd."transaction_id",
  sd."date",
  pc."product_name",
  pc."product_category",
  sd."sales_amount"
FROM
  "company_data"."sales_data" sd
INNER JOIN "company_data"."product_catalog" pc
  ON sd."product_id" = pc."product_id"
WHERE
  pc."product_category" = 'Electronics'
  AND sd."date" > '2023-01-01'
```

Through this query, we integrate data from both datasets based on a shared `product_id`, focusing on 'Electronics' products sold since the start of 2023.

### Tips for Effective Use of Join Filters

- **Attribute Alignments:** Ensure the attributes used in the join condition have a logical correspondence, such as IDs or timestamps.
- **Data Consistency:** Verify that data formats and value ranges align across datasets to prevent mismatches or incorrect join results.
- **Performance Considerations:** Be mindful of the dataset sizes and join complexity, as they can impact query performance. Utilize indexing or consider narrowing the data scope if needed.

### Conclusion

The NQL join filter functionality in Data Studio enhances your ability to interact with and analyze multiple datasets concurrently, ultimately elevating your data storytelling capabilities. By effectively using join operations, you can uncover deeper insights, identify trends, and make data-driven decisions with greater accuracy.

Explore the power of Data Studio and its advanced NQL features today by visiting the [Data Studio UI](https://app.narrative.io/platform/data-studio) and taking your data projects to the next level.
