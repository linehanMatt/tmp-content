---
title: 'Understanding NQL Editor in Data Studio UI'
description: 'The Data Studio UI is tailored to facilitate the use of Narrative Query Language (NQL) for various data operations within the Narrative Data Collaboration Platform.'
lastUpdated: '2023-12-13T19:46:57.570Z'
tags: ['NQL', 'Welcome Guide']
---
### **Query Interface**

* **NQL Editor**: This is where users input their NQL code. The editor supports syntax highlighting to distinguish between different elements of the query language, and provides formatting options to ensure that queries are well-organized and easy to read.
* **Validation and Execution**: Before executing a query, users can Validate to check for errors.

 ![](https://solutions.narrative.io/hubfs/Screenshot%202023-12-13%20at%202-45-29%20PM-png.png)

### **Action Items**

The execution commands, available in the dropdown under Validate, include the option to Run which executes the raw NQL. Alternatively Narrative will add a wrapper around the NQL when one of the following is selected:

* EXPLAIN: The UI provides forecasting as a tool for finding row counts ahead of creating datasets. Finding out counts can help manage the costs associated with running queries.
* Create Materialized View: Users can create materialized views directly from the UI. This feature allows the storage of query results in the form of a dataset.

### **Feedback and Interaction**

* **Assistance**: The 'Ask Rosetta' function is available to guide users through query construction and to understand data attributes. This interactive feature offers assistance in real-time.
* **Interactive Examples**: The UI includes a sample query as an example for formatting. Select “see query” to populate NQL in the text editor.
* **Error Identification**: As queries are input, the UI provides immediate feedback on syntax errors or logical issues, enabling quick troubleshooting. Validation errors also populate in a modal if the NQL query is invalid.

### **API Integration**

While the UI offers a comprehensive environment for building and running queries, users can also access Data Studio's functionalities programmatically via the API, which supports operations like executing, parsing, and compiling NQL queries.
