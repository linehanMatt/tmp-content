---
title: 'Forecasting In Seller Studio'
description: 'Run Forecasts on Your Own Data Before Pushing to Sell Side Endpoints'
lastUpdated: '2022-12-21T01:19:04.574Z'
tags: ['Selling Data', 'Seller Studio']
---
### Background 

The forecasting feature enables users to understand the volume of data that is available for a specific query. This is particularly useful for buyers, who can use forecasting to inform their purchasing decisions. For example, if a user runs a forecast and determines that there is insufficient data to meet their specifications, they can avoid activating a subscription that would not be useful to them. Similarly, sellers can use forecasting to gain insights into the volume and cost of their own data streams, allowing them to make informed decisions about pricing and availability. Overall, forecasting provides a valuable tool for both buyers and sellers to optimize their data-related decision-making processes.

### Seller Studio Forecasting 

Seller Studio Forecasting helps providers optimize their data stream configuration and troubleshoot any issues that may arise, ensuring the smooth operation of their business. Forecasting provides insights for sellers who want to: 

*   Make informed decisions about the processing costs associated with their data streams, helping them to understand the financial implications of offering their data on the marketplace.
*   Anticipate the size of the data stream, allowing them to make informed decisions about pricing and revenue.
*   Validate that the rows behind the potential data stream matches their understanding of internal data volume. 

### Seller Studio Forecasting Workflow

The forecasting feature is accessible within the Seller Studio app by navigating to the "New Data Stream" workflow. To use the tool, users simply need to launch Seller Studio, select the "New Data Stream" button, and choose the dataset they wish to forecast. Sellers should be presented with a screen similar to the following:  

### ![](https://solutions.narrative.io/hubfs/Screenshot%202022-12-20%20at%206-51-37%20PM-png.png)

Next, Seller Studio will then display a screen where users can mark relevant columns as deliverable or filterable. Deliverable columns will be included in the data stream's output schema, while filterable columns allow users to narrow down the available rows. It is important for sellers to carefully consider which columns to mark as deliverable or filterable in order to optimize the value and usability of their data streams.

To generate a forecast for their data stream, providers can simply scroll to the top of the screen and select the "Generate Forecast" button. This will activate the forecasting tool, which will analyze the data stream to provide insight into the volume of data available. The "Data Scanned" section displays the total volume of data behind the dataset used to create the stream, while the "Deliverable Data" section shows the number of rows that meet the column and filter criteria specified during the stream creation process. After a few minutes, the forecast should return results: 

![](https://solutions.narrative.io/hubfs/Screenshot%202022-12-20%20at%206-55-50%20PM-png.png)

The results of the forecasting tool can be a valuable resource for sellers as they plan their data streams. For instance, if the number of deliverable rows is lower than expected, users may want to consider adjusting their filters to include a wider range of data. Alternatively, if the data scanned count is lower than anticipated, the provider may need to ensure that all relevant data has been correctly ingested into the Dataset Manager. By carefully analyzing the results of the forecast, sellers can make informed decisions about their data streams and identify any potential issues or opportunities for improvement.

Next, users should select the relevant endpoints for their data streams. Once a user has selected each endpoint, added a cpm, and continued to the review step, they should see a total cost for buyers that want to purchase the data stream in each channel. This number is calculated from the user inputted cpm and forecasted deliverable rows.  

![](https://solutions.narrative.io/hubfs/Screenshot%202022-12-20%20at%207-56-32%20PM-png.png)

After selecting the relevant endpoints for their data streams, users can specify a cost-per-thousand (CPM) for each endpoint and proceed to the review step. At this point, they will see a total cost for buyers who wish to purchase the data stream in each channel. This cost is calculated based on the user-specified CPM and the forecasted number of deliverable rows. It is important for sellers to carefully consider the pricing of their data streams in order to ensure that they are competitive and attractive to potential buyers.
