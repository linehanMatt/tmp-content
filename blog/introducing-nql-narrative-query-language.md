---
title: 'Introducing NQL: A Powerful Query Language for the Narrative Data Collaboration Platform'
description: 'As businesses grapple with intricate data-driven demands, NQL emerges as the solution for data interoperability and standardization.'
publishDate: '2023-10-24 23:04:28'
author: 'Uri Bushey'
ogImage: '/img/blog/2023/10/nql.png'
image: '/img/blog/2023/10/nql.png'
tags: ['a.i.', 'data collaboration', 'nql', 'data standardization', 'rosetta stone']
authorSlug: 'uri-bushey'
---
We're thrilled to introduce the Narrative Query Language (NQL)—a groundbreaking SQL interface that transforms your data experience on the Narrative Platform. Combined with our Rosetta Stone Attribute Catalog, NQL lets you query shareable or purchasable data from across the entire ecosystem as if it's all housed in your own database. Say goodbye to data silos and hello to limitless insights!

### What is NQL?

NQL is designed to work seamlessly with the existing architecture of the Narrative Data Collaboration Platform. It allows you to query data in a streamlined and intuitive manner, empowering both seasoned data scientists and SQL newcomers to derive meaningful insights from their data and the marketplace of datasets with ease.

### Rosetta Stone Attribute Catalog

One of NQL's standout features is its integration with the Rosetta Stone global attribute catalog. This catalog serves as a central repository for normalized data attributes, aggregated from multiple sources across any company on the platform that has set up an Access Rule. Whether you're querying data from your own company or another that has granted you access, the Rosetta Stone catalog simplifies your data querying process.

### Understanding Normalization with Rosetta Stone Attributes

Different data sources often label things differently. For example, one might use 'M' or 'F' to indicate gender, while another uses true/false values. Rosetta Stone's universal translator makes sure everyone's speaking the same language, so you don't have to worry about it.

### The Magic of Rosetta Stone Attributes

Narrative's Rosetta Stone Attribute technology are what really sets NQL apart. Imagine querying data from multiple organizations as if it all lives in your own table, normalized and ready for analysis. No need to juggle different formats or schemas. Rosetta Stone Attributes make it seamless.

### Example: Querying Rosetta Stone Attributes in NQL

To showcase the power of NQL, let's execute a query that filters data sourced from multiple suppliers on the platform based on gender and a specific event timestamp, while also considering cost control.

{% module\_block module "widget\_1687369202612" %}{% module\_attribute "change\_image\_image\_1" is\_json="true" %}{% raw %}{"alt":"Screenshot 2023-10-24 at 6.50.47 PM-1","height":522,"src":"https://solutions.narrative.io/hubfs/Screenshot%202023-10-24%20at%206.50.47%20PM-1.png","width":1150}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "change\_image\_image\_2" is\_json="true" %}{% raw %}{"src":""}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "change\_image\_link" is\_json="true" %}{% raw %}""{% endraw %}{% end\_module\_attribute %}{% module\_attribute "change\_image\_link\_new\_tab" is\_json="true" %}{% raw %}true{% endraw %}{% end\_module\_attribute %}{% module\_attribute "child\_css" is\_json="true" %}{% raw %}{}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "css" is\_json="true" %}{% raw %}{}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "definition\_id" is\_json="true" %}{% raw %}null{% endraw %}{% end\_module\_attribute %}{% module\_attribute "field\_types" is\_json="true" %}{% raw %}{"change\_image\_link\_new\_tab":"boolean","change\_image\_link\_class":"text","change\_image\_link\_title":"text","change\_image\_link":"text","change\_image\_category":"text","change\_image\_image\_1":"image","change\_image\_image\_2":"image","change\_image\_custom\_class":"text","change\_image\_link\_text":"text"}{% endraw %}{% end\_module\_attribute %}{% module\_attribute "label" is\_json="true" %}{% raw %}null{% endraw %}{% end\_module\_attribute %}{% module\_attribute "module\_id" is\_json="true" %}{% raw %}26006061910{% endraw %}{% end\_module\_attribute %}{% module\_attribute "path" is\_json="true" %}{% raw %}"/Marketplace/Neambo/Act21/Custom\_Modules/Act21 Change Image"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "schema\_version" is\_json="true" %}{% raw %}2{% endraw %}{% end\_module\_attribute %}{% module\_attribute "smart\_objects" is\_json="true" %}{% raw %}null{% endraw %}{% end\_module\_attribute %}{% module\_attribute "smart\_type" is\_json="true" %}{% raw %}"NOT\_SMART"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "tag" is\_json="true" %}{% raw %}"module"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "type" is\_json="true" %}{% raw %}"module"{% endraw %}{% end\_module\_attribute %}{% module\_attribute "wrap\_field\_tag" is\_json="true" %}{% raw %}"div"{% endraw %}{% end\_module\_attribute %}{% end\_module\_block %}

### In this query, we:

Rosetta offers a plethora of benefits. Here are several that stand out:

1.  Use \`EXPLAIN\` to forecast the query's cost and data.  
      
    
2.  Select the "unique\_id" and "gender" attributes from the narrative.rosetta\_stone table, which represents any dataset on the platform that has been mapped to these attributes.  
      
    
3.  Filter the results to include only records with a gender value of 'female'.  
      
    
4.  Further filter by events that occurred after October 1, 2023.  
      
    
5.  Limit cost by specifying a maximum CPM of 2.0 USD.

By leveraging Rosetta Stone Attributes, we can streamline complex queries and make data collaboration simple and efficient.

[Start using Narrative's full data collaboration platform.](https://www.narrative.io/demo)
