---
title: 'Buyer Studio: Re-scan Data to Match Against Newly Appended Input Rows'
description: 'Use the Ingestion Timestamp and Re-scan Data filters to rescan supplier data to match against appended rows to an input Join Dataset filter. '
lastUpdated: '2022-11-02T18:15:33.991Z'
tags: ['Buying Data', 'Buyer Studio']
---
### Overview 

#### Background

By default, Narrative's buy-side apps will only scan net-new data during each subsequent run of a subscription. For example, a buyer places an order with a daily delivery cadence on Tuesday and receives rows from five different suppliers. On Wednesday, the subscription will check for more data by **only scanning net-new data** in any of the relevant datasets and none of the data that was available on Tuesday. As a result, a buyer's processing costs are lower because Narrative does not have to re-scan data to find relevant rows, only net-new rows are considered for subsequent deliveries.

However, **buyers may want to re-scan data to match against new rows in their input dataset.** For example, a buyer creates a subscription on Tuesday with a Join Dataset filter on the unique identifier attribute and a Required filter on the gender attribute. On Wednesday the buyer appends rows to that dataset through Dataset Manager. **Without the Ingestion Timestamp and Re-scan Data filters, the appended rows in the input dataset only have a chance to match against net-new data from suppliers (data added since Tuesday).** This subscription set up will leave out a vast majority of potential matches. 

#### Re-scan Data Filter 

Narrative added the Ingestion Timestamp and Re-scan Data filters to allow users to re-scan data and prevent missed matches. The Ingestion Timestamp filter looks at the moment in time that a row was ingested through Dataset Manager. The ingestion timestamp is different than the event timestamp attribute, which indicates the moment in time in which a supplier gathered their record. The ingestion timestamp will always be more recent than the event timestamp. The filter's range can be a set start date and end date or an ongoing rolling lookback window. The Re-scan Data toggle indicates that the buyer wants to re-scan a certain amount of data to find more matches. Instead of just scanning net-new rows, Narrative will rescan all the data it scanned on the previous delivery in addition to any net new rows. 

The Ingestion Timestamp and Re-scan Data filters should be used in tandem in order to prevent the buyer from re-scanning everything that meets the relevant attribute criteria. The buyer should indicate how far back they want to re-scan using the Ingestion Timestamp filter and then toggle on the Re-scan Data filter to actually re-scan the relevant data. While Narrative does partition data efficiently, the Ingestion Timestamp filter is the only way to ensure that excess data is not re-scanned. 

### Workflow 

1.  The Ingestion Timestamp and Re-scan Data filters are located in the "Filters" step of Buyer Studio  
      
    ![](https://solutions.narrative.io/hubfs/Screen%20Shot%202022-11-02%20at%209-39-07%20AM-png.png)

1.  Select the "Show Advanced Filters" button
2.  Change the "Ingestion Timestamp" Filter from "No Ingestion Filter" to "Custom"   
    
    1.  Set a start date and end date to re-scan the same calendar days during each subsequent delivery   
          
        ![](https://solutions.narrative.io/hubfs/Screen%20Shot%202022-11-02%20at%2010-12-49%20AM-png.png)  
          
        
    2.  Set a rolling lookback to re-scan a set number of days, with the delivery day determining which days to scan.   
          
        ![](https://solutions.narrative.io/hubfs/Screen%20Shot%202022-11-02%20at%2010-37-52%20AM-png.png)  
        \*_note that the the combination of a rolling lookback and a set date range will decrease the number of days re-scanned during each subsequent delivery. Only the overlap of the rolling lookback and the set date range will be re-scanned.\*_ 
    3.  Toggle on the Re-scan Data filter to indicate that each run of the subscription should re-scan all the data available for those attributes, not just net-new data.   
          
        ![](https://solutions.narrative.io/hubfs/Screen%20Shot%202022-11-02%20at%2010-41-50%20AM-png.png)
    
    The order is now ready to re-scan data for a specific timeframe! Please reach out to support@narrative.io with any questions.
