---
title: 'Analyzing Customer Brand Switching Behavior with NQL'
description: 'Learn how Narrative is powering brands to unlock sku level compeitive analysis'
lastUpdated: '2024-29-24'
tags: ['Solution Guide', 'Retail Data']
---


### Introduction
In the competitive landscape of retail, understanding customer behavior, especially in terms of brand loyalty and switching, is crucial. With Narrative Query Language (NQL), businesses have a powerful tool at their disposal to unlock insights into these patterns, enabling them to make data-driven decisions to improve product competitiveness, marketing strategies, and customer retention efforts.

### Use Case 
Consider a retail company aiming to explore customer purchase history to identify instances of brand switching. The goal is to track customers who initially purchased a product but later opted for a competitor's offering within a specified period. Insights gleaned from this analysis are pivotal for assessing product competitiveness, refining marketing initiatives, and addressing product features that may contribute to customer churn.

### Deep Dive into the NQL Query
The NQL query employed for this analysis is structured as follows:

```sql
SELECT a."unique_id"
FROM company_data."brand_data" a
INNER JOIN company_data."brand_data" b ON a."unique_id" = b."unique_id" AND a."timestamp" < b."timestamp"
WHERE a."product_brands" = 'original_product'
AND b."product_brands" IN ('competitor_product_#1', 'competitor_product_#2', 'competitor_product_#3', 'competitor_product_#4', 'competitor_product_#5', 'competitor_product_#6')
```

Let's break down the components of this query to understand its functionality better:

- **SELECT a."unique_id"**: This line retrieves the unique identifiers (such as hashed emails) of customers. These identifiers are essential for tracking individual customer behaviors without compromising their privacy.

- **FROM company_data."brand_data" a**: Specifies the source of the data, in this case, a table named 'brand_data' within a broader dataset labeled 'company_data'. This table contains detailed records of customer purchases, including product brand names and purchase timestamps.

- **INNER JOIN company_data."brand_data" b**: This performs a self-join on the 'brand_data' table, allowing for the comparison of different purchase records within the same table. The alias 'a' represents the initial purchase, and 'b' represents a subsequent purchase by the same customer.

- **ON a."unique_id" = b."unique_id" AND a."timestamp" < b."timestamp"**: These conditions ensure that the analysis only considers cases where two purchases were made by the same customer and the purchase of the competitor's product occurred after the original product purchase.

- **WHERE a."product_brands" = 'original_product'**: Filters the records to only include those where the customer's first purchase was the original product of interest.

- **AND b."product_brands" IN (...)**: Specifies the competitor products, allowing the query to identify customers who switched to any of these specified brands after their initial purchase.

### Insights from Query Results
The result of executing this query is a dataset of unique customer identifiers who have demonstrated brand-switching behavior. This information is invaluable for developing targeted customer retention strategies, such as personalized marketing campaigns or loyalty programs, aimed at mitigating defection to competitors.

### Further Analysis for Enhanced Understanding
Following the identification of customers who have switched brands, further analysis can be conducted to:

- Investigate the reasons behind brand switching, potentially through direct customer feedback or surveys.
- Examine which product categories are most susceptible to customer defection.
- Determine the timing of brand switching to identify patterns or trends that could inform targeted interventions.

### Conclusion
Employing NQL for the analysis of customer brand switching offers businesses a clear and efficient method to derive actionable insights from their data. By dissecting customer purchasing behaviors, companies are better equipped to tailor their products, marketing efforts, and customer engagement strategies to address the underlying factors influencing brand loyalty. This approach not only enhances customer satisfaction and retention but also strengthens the company's competitive position in the market.