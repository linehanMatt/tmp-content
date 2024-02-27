---
title: 'The Power of Query Builder'
description: 'Query Builder is an intuitive, user-friendly interface designed to simplify the complexities of big data querying for users of all skill levels.'
publishDate: '2024-02-26 15:27:10'
author: 'Matt Linehan'
ogImage: '/img/blog/2024/02/the-power-of-query-builder.png'
image: '/img/blog/2024/02/the-power-of-query-builder.png'
tags: ['data collaboration', 'data standardization', 'identity resolution', 'rosetta stone']
authorSlug: 'matt-linehan'
---

Welcome to the future of data querying at Narrative I/O, where we're thrilled to unveil Query Builder: an intuitive, user-friendly interface designed to simplify the complexities of big data querying for users of all skill levels. This innovative tool is poised to transform how you interact with data within the Narrative ecosystem, making data querying seamless, whether it's from your own company datasets or from third-party sources.

### **Simplified Data Querying for Everyone**

While Query Builder is designed to simplify the data querying process, the power of NQL (Narrative Query Language) underpins its operations, offering unparalleled flexibility and precision. NQL allows users to articulate complex data requirements with accuracy, enabling sophisticated querying capabilities that can handle nuanced data exploration tasks. Whether you're filtering vast datasets, performing detailed temporal analyses, or specifying intricate data relationships, NQL provides the syntax and structure to execute your queries with confidence.

The integration of Query Builder with NQL means that users can construct their queries visually and then see the corresponding NQL code. This dual approach demystifies NQL for those less familiar, while still offering the depth and flexibility that data professionals appreciate. It's a bridge between simplicity and complexity, ensuring that all users, regardless of their technical background, can harness the full power of Narrative’s data querying capabilities.

### **The Strategic Advantage of Query Builder**

Query Builder isn't just a tool; it's a strategic asset for businesses and data professionals alike. By encapsulating the complexity of NQL and the power of Rosetta into a user-friendly interface, it enables users to:

- **Execute complex queries with ease**: The intuitive UI reduces the learning curve for NQL, making complex data querying accessible to a broader audience.
- **Enhance data discovery**: With Rosetta Stone, users can explore and integrate a wider range of data sources, opening new avenues for insight and analysis.
- **Accelerate decision-making**: Quick sample data generation and forecast capabilities allow for rapid iteration and refinement of queries, speeding up the data exploration process and enabling faster decision-making.
- **Optimize data spending**: The ability to set budgetary limits within queries ensures that data acquisition costs are aligned with business priorities and constraints.

### **Step-by-Step Workflow**
<br>

<img src="/img/blog/2024/02/query-builder-1.png" alt="image" width="800" height="auto">
<br>

- **Select Your Data Source**: Kickstart your query by choosing "My Data" for personal datasets or "Rosetta Stone" for third-party data. This choice tailors your querying journey right from the start.
- **Configure Output Columns**: Decide which data columns you need. Whether it’s field from your datasets or Rosetta Stone attributes, this step customizes the output to your specific schema requirements.
- **Apply Filters with Precision**: Refine your query with filters, using operators to narrow down by geography, time frames, and more. It’s about getting the data that matters most to you.
- **Control Your Budget**: Set limits on how much you're willing to spend on your queries, ensuring you get the insights you need without overspending.

### **From NQL to Query Builder**

Imagine crafting a query that sifts through global data to pinpoint specific trends, all within a budget you define. Query Builder makes this possible through an intuitive interface, transforming this:

```sql
SELECT
  narrative.rosetta_stone."unique_id"."value",
  narrative.rosetta_stone."iso_3166_1_country"
FROM
  narrative.rosetta_stone
WHERE
  (
    narrative.rosetta_stone."iso_3166_1_country" = 'US'
    AND
    narrative.rosetta_stone."event_timestamp" BETWEEN
    '2024-02-01' AND '2024-02-21'
  )
LIMIT
  300 USD PER CALENDAR_MONTH
```

Into a user-friendly, straightforward process that demystifies data querying without sacrificing the depth or breadth of your data exploration:

<br>

<img src="/img/blog/2024/02/query-builder-2.png" alt="image" width="800" height="auto">
<br>

### **Leveraging Rosetta: Your Data Querying Assistant**

Within Query Builder’s environment, Rosetta acts as your intelligent assistant, designed to streamline the query creation process. By selecting the "Ask Rosetta" button at any point in Query Builder’s workflow, users can articulate their query needs in plain English. Rosetta then interprets these requirements, translating them into precise NQL. This unique feature not only enhances the user experience but also serves as an educational tool, bridging the gap between conceptual data queries and their technical execution.

### **From Query to Action**

After crafting a query using Query Builder, users are presented with several powerful options to finalize their data exploration journey:

- **Sample Run**: Before committing resources, users can execute a sample run of their query. This provides a sneak peek into the output and sample rows, ensuring the query aligns with their expectations and objectives.
- **Forecasting**: To gauge the scope and potential cost of a query, users can opt for a forecast run. This feature estimates the number of rows matching the query parameters and the associated costs, offering valuable insights for budget planning.
- **Dataset Creation**: Once satisfied with the query's setup and its forecasted impact, users can proceed to run the query, resulting in the creation of a new dataset.

### **Pushing to a Destination**

The journey doesn't end with dataset creation. Narrative I/O offers users the option to push their curated datasets to various destinations, amplifying the value and utility of their data. Whether it's cloud storage solutions like AWS S3 buckets or activation platforms such as Facebook and Trade Desk, users can seamlessly transfer their datasets, ensuring their insights are actionable and integrated within their broader data strategy. This final step in Query Builder’s workflow exemplifies Narrative I/O's holistic approach to data management, from query creation to real-world application.

### **Conclusion**

Narrative I/O's Query Builder, augmented by the intelligent assistance of Rosetta and the comprehensive capabilities of the Rosetta Stone attribute library, offers an unparalleled platform for data querying. It's designed to democratize data exploration, making it accessible, intuitive, and impactful for users of all backgrounds. By simplifying complex data interactions and providing pathways to actionable insights, Narrative I/O reaffirms its position as a leader in data innovation. Query Builder is more than just a tool; it's a gateway to unlocking the potential of your data, designed to foster informed decision-making and strategic advantage in today's data-driven world.
