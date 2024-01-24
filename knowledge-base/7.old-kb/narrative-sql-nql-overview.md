---
title: 'Narrative Query Language (NQL): Overview'
description: 'Narrative Query Language (NQL) is a specialized query language designed for the Narrative Data Collaboration Platform. Use NQL to perform queries on datasets, forecast for available data, and more. '
lastUpdated: '2023-12-28T15:57:21.944Z'
tags: ['NQL', 'Welcome Guide']
---
#### Quickstart

Get started with NQL by running some simple queries:

**Find rows containing gender='female':**

EXPLAIN  
SELECT  
  narrative.rosetta\_stone."unique\_id"."value",  
  narrative.rosetta\_stone."hl7\_gender"."gender"  
FROM  
  narrative.rosetta\_stone  
WHERE  
  narrative.rosetta\_stone."hl7\_gender"."gender" = 'female'  
  AND narrative.rosetta\_stone."event\_timestamp" > '2023-10-01'  
  AND narrative.rosetta\_stone.\_price\_cpm\_usd <= 2.0;  
  

#### NQL Query Editor in Data Studio UI

The NQL Query Editor is integrated into the Data Studio UI. This feature allows you to write queries starting with the SELECT statement and execute them either as a forecast (EXPLAIN), or by creating a new dataset from the output of your query (CREATE MATERIALIZED VIEW).

Navigate to the NQL Query Editor [here](https://app.narrative.io/platform/data-studio).

#### Datasets

NQL operates on one or more datasets. You can reference your own company's data by querying the special namespace schema company\_data. [Learn more about Datasets](https://kb.narrative.io/how-narrative-works-introduction).

Each dataset must be made accessible via Access Rules. Access rules determine who can query a dataset and at what price. [Learn more about Access Rules](https://kb.narrative.io/how-narrative-works-introduction).

You need to have an access rule in place to query any dataset, even if you own the dataset.

Example:

SELECT  
  company\_data."20"."Workout\_Timestamp",  
  company\_data."20"."Total\_Output" AS output  
FROM  
  company\_data."20"  
  

#### Rosetta Stone Attributes

The Narrative platform features a standardized global data attribute catalog called "Rosetta Stone." Elements of the Rosetta Stone catalog are organized into attributes, which can be simple attribute types such as numbers or strings, or more complex objects containing multiple properties.

When querying a Rosetta Stone attribute, you use the specialized namespace "rosetta\_stone" and refer to the attribute by name.

Example:

SELECT narrative.rosetta\_stone."event\_timestamp"

When querying attributes that are of type object, you must refer to the child properties directly (you cannot select the attribute itself without referring to at least one property.)

Example:

SELECT narrative.rosetta\_stone."unique\_id"."value",  
       narrative.rosetta\_stone."unique\_id"."type"

You can query these attributes if the underlying dataset has been exposed to you by an appropriate Access Rule. Learn more about [Rosetta Stone Attributes](https://kb.narrative.io/how-rosetta-stone-works).

#### Access Rules

Access Rules regulate query permissions, specifying datasets, authorized users, queryable fields, pricing, and additional constraints. Learn more about [Access Rules](https://kb.narrative.io/how-access-rules-work).

#### Identifiers

### Reserved Fields

*   \_price\_cpm\_usd: Specifies the maximum cost-per-mille (CPM) in US Dollars that you are willing to pay for 1000 rows of data. Setting this to 0 explicitly filters out access rules with a price, querying only free data. Omitting a CPM filter applies no filter, allowing targeting of data at any price.

### Identifier Rules

*   Use double quotes for identifiers
*   NQL operates in "strict mode"; identifiers must be fully qualified

#### Query Features

### Cost Control

Control query costs by filtering on unit price per thousand rows (\_price\_cpm\_usd) or setting an overall budget for the query (LIMIT).

SELECT \[...\] WHERE \[...table.column <filter\_expression>\] \[\_price\_cpm\_usd <= <price>\] \[LIMIT 100.50 USD PER CALENDAR\_MONTH\]  
  

Setting \_price\_cpm\_usd to 0 filters out access rules with a price, querying only free data. Omitting a CPM filter applies no filter, allowing targeting of data at any price.

Specifying LIMIT 0 USD PER CALENDAR\_MONTH implies purchasing only data with zero cost, and if LIMIT is not included, a limit of 0 is assumed. To specify no budget constraint, use NO LIMIT.

### Data and Cost Forecasting

Use EXPLAIN <query> to generate a forecast.

Forecasts return information about the amount of data that will be returned from running a query, as well as the price to execute the query itself and the cost of querying the data (if relevant).

### Creating Materialized Views

In NQL, creating a materialized view not only caches query results but also creates a new, unique dataset within the Narrative Data Collaboration Platform. Unlike typical databases where materialized views are used to cache expensive query results for performance improvement, in NQL, these views result in a net new dataset.

Creating a materialized view effectively creates a new dataset with a unique name. Such datasets cannot ingest data from other sources. Data purchase costs may or may not be incurred when executing a query that materializes data as a new dataset, depending on the underlying query's access rules.

Example Query:

CREATE MATERIALIZED VIEW "sports\_events"  
  DISPLAY\_NAME = 'Sports Events View'  
  DESCRIPTION = 'This view contains data for sports events with a timestamp greater than 2023-10-05, where the sports team is not null, and the price CPM in USD is less than or equal to 2.0.'  
  EXPIRE = 'P90D'  
  STATUS = 'active'  
  TAGS = ('sports', 'events')  
  WRITE\_MODE = 'append'  
  EXTENDED\_STATS = 'all'  
  PARTITIONED\_BY narrative.rosetta\_stone.event\_timestamp DAY  
  REFRESH\_SCHEDULE = '@daily'    
AS  
SELECT  
  narrative.rosetta\_stone.unique\_id,  
  narrative.rosetta\_stone.sports\_team,  
  narrative.rosetta\_stone.event\_timestamp  
FROM  
  narrative.rosetta\_stone  
WHERE  
  narrative.rosetta\_stone.event\_timestamp > '2023-10-05'  
  AND narrative.rosetta\_stone.sports\_team IS NOT NULL  
  AND narrative.rosetta\_stone.\_price\_cpm\_usd <= 2.0  
LIMIT  
  50 USD PER CALENDAR\_MONTH  
  

**Metadata Options**

The following metadata is applied to the dataset that is created as a result of the CREATE MATERIALIZED VIEW command. These settings may be mutable, so they are not stored in the query after the initial execution; after executing the command, these settings can be accessed and modified using the Dataset API.

DISPLAY\_NAME: A user-friendly name for the materialized view.

DESCRIPTION: Provides a clear explanation of the view's content and purpose.

EXPIRE: Sets the expiration period for the view in ISO 8601 format. Default is to retain\_everything. Allowed Values:

*   expireWhen > ISO PERIOD
*   retain\_everything
*   expire\_everything

STATUS: Indicates the current status of the view, such as 'active'.

TAGS: A set of identifiers for categorization or referencing, with '\_nio\_materialized\_view' always included.

WRITE\_MODE: Determines how new data is added to the view, either 'append' or 'overwrite'. Default is append.

EXTENDED\_STATS: Specifies whether to include extended statistics ('all' or 'none'). Default is 'all'.

PARTITIONED\_BY: Allows partitioning of the view for efficient querying, with the default partition always present. Additional partitions can be specified with the format <field> <transform>.

REFRESH\_SCHEDULE: Defines the frequency of updates for the view. Accepts cron expressions or enums ('@hourly', '@daily', '@weekly', '@monthly', '@once'). 

### **Querying an Access Rule Directly**

An access rule has two identifiers: an \`access\_rule\_name\` and an \`access\_rule\_id\`. Access rule names are human readable and must be created explicitly, while access rule ids are created automatically during the initial set up for each access rule. NQL supports querying access rules directly through \`access\_rule\_name\` and not \`access\_rule\_id\`.

  

NQL supports querying internal access rules (access rules on datasets in the same company seat) or external access rules (access rules on datasets in a different company seat) directly. Querying an access rule is the third method of querying datasets in NQL, in addition to the Rosetta Stone attribute catalog and dataset ids.

**Querying Internal Access Rules**

An access rule name is added after the company identifier. When querying data in your own company seat, an access rule name always follows \`company\_data\`.

SELECT pd.hashed\_emails  
FROM company\_data.access\_rule\_for\_private\_deal pd

**Querying External Access Rules**

An access rule name is added after the company identifier. When querying data in your own company seat, an access rule name always follows \`company\_slug\`.

SELECT teams.baseball\_teams  
FROM company\_slug.access\_rule\_unique\_name\_1 teams

### Embedded Namespaces in NQL - \_rosetta\_stone

NQL supports attribute querying via the Rosetta Embedded Namespace. This namespace is facilitated by \`\_rosetta\_stone\`, a direct method to query Rosetta Stone attributes. \`\_rosetta\_stone\` acts as an attribute reference within the dataset or access rule. \`\_rosetta\_stone\` must follow either a dataset's \`unique\_name\`, a dataset's \`id\`, or an access rule's \`name\`. In case of an absence of mappings or an incorrect attribute reference, the query will return an error.

**Basic Usage**

SELECT ds\_identifier.\_rosetta\_stone."attribute\_name" AS alias\_name  
FROM dataset\_source

*   ds\_identifier: Alias or identifier for the dataset. A dataset can be referenced by its id or unique\_name.
*   attribute\_name: The name of the Rosetta Stone attribute to be mapped.
*   alias\_name: An optional alias for the selected attribute.

**Example with Single Dataset**

    SELECT ds\_123.\_rosetta\_stone."event\_timestamp" AS event\_time  
    FROM company\_data.ds\_123 AS ds\_123

**Example with Joining Multiple Datasets**

 SELECT  
        ds\_123.\_rosetta\_stone."attribute\_1" AS attribute\_from\_a,  
        ds\_456.\_rosetta\_stone."attribute\_2" AS attribute\_from\_b,  
        ds\_123.email,  
        ds\_456.username  
    FROM  
        company\_data.ds\_123 AS ds\_123  
    JOIN  
        company\_data.ds\_456 AS ds\_456  
    ON  
        ds\_123.user\_id = ds\_456.user\_id

In this example:

*   The first Rosetta Stone attribute (attribute\_1) is being pulled from dataset ds\_123.
*   The second Rosetta Stone attribute (attribute\_2) is being pulled from dataset ds\_456.

Example with Nested Properties

    SELECT  
        ds\_123.\_rosetta\_stone."nested"."attribute" AS nested\_attribute  
    FROM  
        company\_data.ds\_123 AS ds\_123

*   For nested properties, the same dot notation is used within the \_rosetta\_stone namespace.

**Example with Filtering With Rosetta Attributes**

SELECT  
  ds\_123.\_rosetta\_stone."unique\_id"."value" AS id  
FROM  
  company\_data.ds\_123 AS ds\_123  
WHERE  
  ds\_123.id = 123

*   Here, the WHERE clause uses the Rosetta attribute unique\_id.value from dataset ds\_123 for filtering.

#### API and API References

API Services

See full details in our [API Documentation](https://api.narrative.dev/)

*   /nql/run: Executes the NQL query.
*   /nql/parse: Parses NQL syntax.
*   /nql/compile: Compiles the NQL query into the underlying SQL engine, but does not execute the comand.

#### See Also

*   [How Narrative Works](https://kb.narrative.io/how-narrative-works-introduction)
