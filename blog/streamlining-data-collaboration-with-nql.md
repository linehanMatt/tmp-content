---
title: 'Streamlining Data Collaboration with NQL: Commingling Standardized and Raw Data'
description: 'NQL allows users to effortlessly blend their own data with standardized attributes from first-party and third-party sources in a single query.'
publishDate: '2024-02-22 16:33:10'
author: 'Matt Linehan'
ogImage: '/img/blog/2024/02/collaborating-with-NQL.png'
image: '/img/blog/2024/02/collaborating-with-NQL.png'
tags: ['data collaboration', 'data standardization', 'NQL', 'rosetta stone']
authorSlug: 'matt-linehan'
---
At Narrative, we're constantly pushing the boundaries of data collaboration and efficiency. Our latest release in the Narrative Query Language (NQL) marks a significant leap forward, enabling users to effortlessly blend their own data with standardized attributes from first-party and third-party sources in a single query. This functionality isn't just an upgrade; it's a revolution in how data scientists, engineers, and product managers manage data across various formats.  

### Rosetta Stone for your data 

The standout feature of this release is the introduction of the _rosetta_stone namespace. This breakthrough allows for seamless access to both the raw column and the normalized 'attribute version' of a column. This means you can compare columns with attributes alongside those without, all in one fluid query, regardless of the original data schema or format.

```sql
SELECT
    my_dataset._rosetta_stone."attribute"
FROM
    company_data.my_dataset AS my_dataset
```
<br>


### Solving Real Business Challenges
<br>

### Scenario: Targeted Marketing Insights

Imagine you're a data scientist at a retail company, tasked with creating a targeted marketing campaign. Your challenge? Combining customer interaction data from your CRM with demographic information from a third-party dataset. In the NQL query below, we leverage the power of Narrative's Rosetta Stone to effortlessly combine diverse datasets for targeted marketing insights. Here's how we simplify the process:

- **Normalized Email Joins**: We use a unified **`hashed_email`** attribute to seamlessly link customer data across different sources. This means no matter how emails are stored across datasets, we can easily match them up.
- **Unified Demographic Attributes**: By tapping into normalized **`gender`** and **`age`** attributes, we integrate varied representations of these demographics into a standard format. This allows us to focus on specific customer segments without worrying about data inconsistencies.
- **Efficient Data Selection**: The query mixes raw data (like **`favorite_store`**) with these standardized demographics, providing a rich, detailed view of our target audience in fewer steps and with less code.

This approach significantly reduces the complexity of joining and analyzing data from multiple sources, making it more accessible to marketers and data scientists looking to gain insights into their customer base.

```sql
SELECT
    your_data._rosetta_stone.hashed_email.value AS my_emails,
    your_data.favorite_store,
    narrative.rosetta_stone.hl7_gender.gender,
    narrative.rosetta_stone.age
FROM
    company_data.my_crm_dataset AS your_data
JOIN
    narrative.rosetta_stone AS third_party_data
ON
    your_data.hashed_email.value = third_party_data.hashed_email.value
WHERE
    third_party_data.gender = 'female'
    AND third_party_data.age BETWEEN 20 AND 30
    AND my_emails IS NOT NULL
```
<br>

### **Technical Excellence, Simplified**
<br>

### Behind the Scenes

Narrative's NQL, akin to SQL, is intuitive and robust. It compiles your NQL statement into the appropriate SQL for various Query Execution Engines like Snowflake SQL and Apache Spark. The normalization of underlying tables to Rosetta Stone attributes occurs at query time, inserting SQL that performs the mapping for you, ensuring data integrity and consistency across disparate sources.

### **Sample Datasets and Automatic Transformations**

To illustrate the power of the **`_rosetta_stone`** namespace, consider these three sample datasets with different schemas/values for age and gender:

1. **Dataset A**: **`Age`** (in years), **`Gender`** (**`M`**/**`F`**)
2. **Dataset B**: **`Age_Group`** (**`18-25`**, **`26-33`**, etc.), **`Sex`** (**`Male`**, **`Female`**)
3. **Dataset C**: **`Age_Range`** (**`Young Adult`**, **`Adult`**, **`Senior`**), **`G`** (**`1`** for male, **`2`** for female)

Narrative's Rosetta Stone automatically transforms these disparate values and column headers into unified **`age`** and **`gender`** attributes, simplifying complex data analysis without manual data wrangling.

### Querying Without NQL

Now, let's contrast this with what the equivalent raw SQL query might look like, using the three sample datasets provided. This will demonstrate the complexity that Narrative's NQL abstracts away.

```sql
WITH normalized_data AS (
  SELECT
    MD5(email) AS hashed_email,
    favorite_store,
    'male' AS gender,
    CAST(SUBSTRING(age, 1, 2) AS INTEGER) AS age
  FROM dataset_a
  WHERE gender = 'M'
  UNION ALL
  SELECT
    MD5(email),
    favorite_store,
    CASE WHEN sex = 'Male' THEN 'male' ELSE 'female' END,
    CASE 
      WHEN age_group = '18-25' THEN 21
      WHEN age_group = '26-33' THEN 29
      ELSE NULL
    END
  FROM dataset_b
  UNION ALL
  SELECT
    MD5(email),
    favorite_store,
    CASE WHEN g = 1 THEN 'male' WHEN g = 2 THEN 'female' ELSE NULL END,
    CASE 
      WHEN age_range = 'Young Adult' THEN 25
      WHEN age_range = 'Adult' THEN 35
      WHEN age_range = 'Senior' THEN 65
      ELSE NULL
    END
  FROM dataset_c
), joined_data AS (
  SELECT
    n.hashed_email,
    n.favorite_store,
    n.gender,
    n.age
  FROM
    normalized_data n
  JOIN
    your_company_data ycd ON n.hashed_email = MD5(ycd.email)
  WHERE
    n.gender = 'female'
    AND n.age BETWEEN 20 AND 30
)

SELECT * FROM joined_data;
```
<br>

This raw SQL example involves complex CASE statements to manually normalize **`gender`** and **`age`** values from different schemas, unions to join all the tables, and a hashing function to match emails across datasets. While the above NQL remains the same if there are 3 tables mapped to age and gender or 100, each additional dataset requires 10+ new lines of SQL to achieve the same output. The example showcases the substantial amount of manual effort and code required to perform operations that Narrative's NQL simplifies dramatically through its Rosetta Stone feature, thus underscoring the value of the NQL approach in streamlining data collaboration and analysis.

### **Understanding Rosetta Stone Namespaces**

- **`narrative.rosetta_stone`**: This is a normalized and standardized union across all datasets, enabling the joining of data on attributes like **`hashed_email`** despite original differences.
- **`company_data._rosetta_stone`**: This refers to the normalized and standardized version of a single column within your company's dataset, aiding in internal data consistency.
- **`company_data.dataset_name`**: Represents the raw value of a single column from your company's data, providing access to unaltered data for specialized analysis.

### **🌟 Leading the Way in Data Collaboration**

Narrative's approach to data collaboration is unparalleled. Our platform's ability to handle complex data structures while maintaining ease of use positions us as a leader in the field. We're not just providing tools; we're crafting solutions that transform how businesses interact with data.

Ready to experience the future of data querying and collaboration? Reach out to your sales representative to schedule a demo. Discover how Narrative's NQL can empower your data strategies and drive your business forward.

Ready to get started? [<ins>Get in touch!</ins>](https://www.narrative.io/contact)
