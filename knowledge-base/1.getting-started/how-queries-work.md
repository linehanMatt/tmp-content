---
title: 'How Queries Work'
description: 'Queries in the Narrative platform identify specific rows of data across one or more datasets, helping you extract the most relevant data for your purposes.'
lastUpdated: '2023-06-09T21:19:57.049Z'
tags: ['Welcome to Narrative', 'How Narrative Works']
---
Queries function similarly to queries in a relational database structure: serving as sets of parameters that pinpoint specific rows of data from one or more datasets.

### **Queries**

Queries are defined by parameters such as filters and attributes. Once set, they delve into the data, retrieving precise information based on your requirements. Depending on the existence of associated jobs, you can either view these jobs or load the query in the Data Studio.

### **Materialized Views**

Materialized views are jobs that run once or on a regular basis to execute a query. Every materialized view outputs data into a new Dataset with a scheme defined by the query. Materialized views that run on a schedule add new data to the existing output dataset by appending to or overwriting data.

### **Forecasts**

Forecasts are estimates that predict the outcome of running a query. They reveal how many rows of data would be delivered, the processing costs to execute a query, and if requested other aggregations such as the suppliers that contribute to a query or aggregate counts. Forecasts can be run either on sampled data, providing a directional estimate of the data that is contained within a query at no cost, or they can be run across all applicable data, offering a precise, point-in-time prediction (which is associated with a processing usage fee).

### **Jobs**

Jobs are tasks within the Narrative's platform. Every operation, like running a forecast or a quer, leads to the creation of a job. Jobs allow for tracking of these operations and their status.  
  
![](https://solutions.narrative.io/hubfs/Screenshot%202023-06-09%20at%205-19-36%20PM-png.png)
