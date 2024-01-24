---
title: 'A deeper dive into NQL - Narrative Query Language'
description: 'Narrative Query Language (NQL) and our Rosetta Stone technology is revolutionary technology.'
publishDate: '2023-10-24 23:26:08'
author: 'Uri Bushey'
ogImage: '/img/blog/2023/10/nql-deep-dive.png'
image: '/img/blog/2023/10/nql-deep-dive.png'
tags: ['a.i.', 'data collaboration', 'nql', 'data standardization', 'rosetta stone']
authorSlug: 'uri-bushey'
---
We're thrilled to announce the Narrative Query Language, or NQL for short. This powerful querying tool allows users to execute queries on the Narrative Data Collaboration Platform with a host of unique features that make data collaboration easier, more secure, and more efficient.  

### The Magic of Rosetta Stone Attributes  

Narrative's Rosetta Stone Attribute technology is what really sets NQL apart. Imagine querying data from multiple organizations as if it all lives in your own table, normalized and ready for analysis. No need to juggle different formats or schemas. Rosetta Stone Attributes make it seamless.  

### Permissions & Access Rules  

NQL takes security seriously. All table permissions are governed by Access Rules, which specify:

*   The dataset in question
*   Authorized users or companies
*   Fields in the dataset that can be queried
*   Any applicable query cost
*   Optional analysis restrictions

By default, users query against all tables they have permission for, as long as the query aligns with these rules.  

### Example: Querying Rosetta Stone Attributes in NQL  

To showcase the power of NQL, let's execute a query that filters data sourced from multiple suppliers on the platform based on gender and a specific event timestamp while also considering cost control.

{% module\_block module "widget\_1687369202612" %}{% module\_attribute "change\_image\_image\_1" is\_json="true" %}{% raw %}{"alt":"Screenshot 2023-10-24 at 6.50.47 PM-1","height":522,"src":"https://solutions.narrative.io/hubfs/Screenshot%202023-10-24%20at%206.50.47%20PM-1.png","width":1150}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "change\_image\_image\_2" is\_json="true" %}{% raw %}{"src":""}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "change\_image\_link" is\_json="true" %}{% raw %}""{% endraw %}{% end\_module\_attribute %}{% module\_attribute "change\_image\_link\_new\_tab" is\_json="true" %}{% raw %}true{% endraw %}{% end\_module\_attribute %}{% module\_attribute "child\_css" is\_json="true" %}{% raw %}{}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "css" is\_json="true" %}{% raw %}{}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "definition\_id" is\_json="true" %}{% raw %}null{% endraw %}{% end\_module\_attribute %}{% module\_attribute "field\_types" is\_json="true" %}{% raw %}{"change\_image\_link\_new\_tab":"boolean","change\_image\_link\_class":"text","change\_image\_link\_title":"text","change\_image\_link":"text","change\_image\_category":"text","change\_image\_image\_1":"image","change\_image\_image\_2":"image","change\_image\_custom\_class":"text","change\_image\_link\_text":"text"}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "label" is\_json="true" %}{% raw %}null{% endraw %}{% end\_module\_attribute %}{% module\_attribute "module\_id" is\_json="true" %}{% raw %}26006061910{% endraw %}{% end\_module\_attribute %}{% module\_attribute "path" is\_json="true" %}{% raw %}"/Marketplace/Neambo/Act21/Custom\_Modules/Act21 Change Image"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "schema\_version" is\_json="true" %}{% raw %}2{% endraw %}{% end\_module\_attribute %}{% module\_attribute "smart\_objects" is\_json="true" %}{% raw %}null{% endraw %}{% end\_module\_attribute %}{% module\_attribute "smart\_type" is\_json="true" %}{% raw %}"NOT\_SMART"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "tag" is\_json="true" %}{% raw %}"module"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "type" is\_json="true" %}{% raw %}"module"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "wrap\_field\_tag" is\_json="true" %}{% raw %}"div"{% endraw %}{% end\_module\_attribute %}{% end\_module\_block %}

### In this query, we:  

*   Use \`EXPLAIN\` to forecast the query's cost and data.
*   Select the "unique\_id" and "gender" attributes from the narrative.rosetta\_stone table, which represents any dataset on the platform that has been mapped to these attributes.
*   Filter the results to include only records with a gender value of 'female'.
*   Further filter by events that occurred after October 1, 2023.
*   Limit cost by specifying a maximum CPM of 2.0 USD.

By leveraging Rosetta Stone Attributes, we can streamline complex queries and make data collaboration simple and efficient.

### Understanding Normalization with Rosetta Stone Attributes  

Rosetta Stone's normalization process allows different datasets to be easily integrated. For example, one dataset might have a column named "gender" with values 'M' or 'F', while another dataset might have a column named "is\_female" with boolean values.  
  

{% module\_block module "widget\_3b41adc8-e4b1-4b60-abd1-96913a6129d5" %}{% module\_attribute "change\_image\_image\_1" is\_json="true" %}{% raw %}{"alt":"rosetta stone standardization","height":530,"src":"https://solutions.narrative.io/hubfs/Screenshot%202023-10-24%20at%207.09.19%20PM.png","width":746}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "change\_image\_image\_2" is\_json="true" %}{% raw %}{"src":""}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "change\_image\_link" is\_json="true" %}{% raw %}""{% endraw %}{% end\_module\_attribute %}{% module\_attribute "change\_image\_link\_new\_tab" is\_json="true" %}{% raw %}true{% endraw %}{% end\_module\_attribute %}{% module\_attribute "child\_css" is\_json="true" %}{% raw %}{}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "css" is\_json="true" %}{% raw %}{}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "definition\_id" is\_json="true" %}{% raw %}null{% endraw %}{% end\_module\_attribute %}{% module\_attribute "field\_types" is\_json="true" %}{% raw %}{"change\_image\_link\_new\_tab":"boolean","change\_image\_link\_class":"text","change\_image\_link\_title":"text","change\_image\_link":"text","change\_image\_category":"text","change\_image\_image\_1":"image","change\_image\_image\_2":"image","change\_image\_custom\_class":"text","change\_image\_link\_text":"text"}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "label" is\_json="true" %}{% raw %}null{% endraw %}{% end\_module\_attribute %}{% module\_attribute "module\_id" is\_json="true" %}{% raw %}26006061910{% endraw %}{% end\_module\_attribute %}{% module\_attribute "path" is\_json="true" %}{% raw %}"/Marketplace/Neambo/Act21/Custom\_Modules/Act21 Change Image"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "schema\_version" is\_json="true" %}{% raw %}2{% endraw %}{% end\_module\_attribute %}{% module\_attribute "smart\_objects" is\_json="true" %}{% raw %}null{% endraw %}{% end\_module\_attribute %}{% module\_attribute "smart\_type" is\_json="true" %}{% raw %}"NOT\_SMART"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "tag" is\_json="true" %}{% raw %}"module"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "type" is\_json="true" %}{% raw %}"module"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "wrap\_field\_tag" is\_json="true" %}{% raw %}"div"{% endraw %}{% end\_module\_attribute %}{% end\_module\_block %}

With NQL, you can query both of these datasets using the Narrative [HL7 Gender Identity](https://app.narrative.io/attributes/h-l-7-gender-identity) attribute, referred to in the NQL statement as "narrative"."rosetta\_stone"."hl7\_gender"."gender". 

### Example: Joining Rosetta Stone with Your Company Data  

Imagine a company that wants to create targeted marketing campaigns for female customers who have interacted with their services after a certain date. This query can pull that specific data from the company's own CRM file and the Rosetta Stone, consolidating information into a single, actionable dataset.

{% module\_block module "widget\_1a6c2c01-cb98-40ec-9d60-acb4418a81a8" %}{% module\_attribute "change\_image\_image\_1" is\_json="true" %}{% raw %}{"alt":"Screenshot 2023-10-24 at 7.18.29 PM-1","height":724,"src":"https://solutions.narrative.io/hubfs/Screenshot%202023-10-24%20at%207.18.29%20PM-1.png","width":1340}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "change\_image\_image\_2" is\_json="true" %}{% raw %}{"src":""}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "change\_image\_link" is\_json="true" %}{% raw %}""{% endraw %}{% end\_module\_attribute %}{% module\_attribute "change\_image\_link\_new\_tab" is\_json="true" %}{% raw %}true{% endraw %}{% end\_module\_attribute %}{% module\_attribute "child\_css" is\_json="true" %}{% raw %}{}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "css" is\_json="true" %}{% raw %}{}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "definition\_id" is\_json="true" %}{% raw %}null{% endraw %}{% end\_module\_attribute %}{% module\_attribute "field\_types" is\_json="true" %}{% raw %}{"change\_image\_link\_new\_tab":"boolean","change\_image\_link\_class":"text","change\_image\_link\_title":"text","change\_image\_link":"text","change\_image\_category":"text","change\_image\_image\_1":"image","change\_image\_image\_2":"image","change\_image\_custom\_class":"text","change\_image\_link\_text":"text"}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "label" is\_json="true" %}{% raw %}null{% endraw %}{% end\_module\_attribute %}{% module\_attribute "module\_id" is\_json="true" %}{% raw %}26006061910{% endraw %}{% end\_module\_attribute %}{% module\_attribute "path" is\_json="true" %}{% raw %}"/Marketplace/Neambo/Act21/Custom\_Modules/Act21 Change Image"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "schema\_version" is\_json="true" %}{% raw %}2{% endraw %}{% end\_module\_attribute %}{% module\_attribute "smart\_objects" is\_json="true" %}{% raw %}null{% endraw %}{% end\_module\_attribute %}{% module\_attribute "smart\_type" is\_json="true" %}{% raw %}"NOT\_SMART"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "tag" is\_json="true" %}{% raw %}"module"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "type" is\_json="true" %}{% raw %}"module"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "wrap\_field\_tag" is\_json="true" %}{% raw %}"div"{% endraw %}{% end\_module\_attribute %}{% end\_module\_block %}

In the example query, the JOIN operation combines data from the narrative.rosetta\_stone dataset (aliased as rs) with the "crm\_file" dataset (aliased as cd). The key point here is that the Rosetta Stone dataset is normalized. This means that the data has been preprocessed and standardized to allow seamless integration with other datasets, such as your company data.

### What is going on behind the scenes  

Behind the scenes, Narrative is compiling your NQL statement down into the appropriate SQL statement for a given Query Execution Engines. We are launching with support for two Execution Engines (Snowflake SQL, and Apache Spark). We are also normalizing all of the underlying tables that are mapped to a Rosetta Stone attribute at query time, inserting SQL that performs the mapping on your behalf.

To learn more, reach out to your sales rep to schedule a demo! 

[Start using Narrative's full data collaboration platform.](https://www.narrative.io/demo)