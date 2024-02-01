---
title: 'Buyer Studio: Frequency Filter'
description: 'Learn how to control the frequency certain data points show up in a subscription. '
lastUpdated: '2021-12-08T20:38:14.256Z'
tags: ['Buying Data', 'Buyer Studio']
---
### Overview 

Buy orders now have a new way to filter the frequency in which an event shows up in a given dataset. The filter creates a minimum and/or maximum range for the amount of times the specific data point must show up in that dataset's column. 

### **Frequency Filters and Deduplication** 

Frequency filtering and deduplication can be used together in the same subscription. However, frequency filtering occurs on the backend after deduplication i.e. frequency filtering happens on the result of deduplication. If two rows are considered duplicates and there is a Deduplication Strategy, the Frequency Filter will only receive one row to filter. 

#### Example 

Here's an example dataset containing just two attributes: IDs and Timestamps  

IDFA10, 10am

IDFA10, 10am

IDFA33, 10am

IDFA33, 11am

IDFA44, 1pm 

A frequency filter of (ID) > 2 and no **deduplication strategy** results in: 

IDFA10, 10am

IDFA10, 10am

IDFA33, 10am

IDFA33, 11am 

A frequency filter of (timestamp) > 2 and no **deduplication strategy** results in: 

IDFA10, 10am

IDFA10, 10am

IDFA33, 10am

A frequency filter of (ID) > 2 and **a deduplication strategy on (timestamp)** results in: 

IDFA33, 10am

IDFA33, 11am

 

Frequency filter can also happen across multiple attributes i.e. (ID, timestamp). The logic looks at the **combination** of the two that is seen N times, not each column independently. For example: using the same dataset from before, a frequency filter of (ID, Timestamp) > 2 results in: 

IDFA10, 10am

IDFA10, 10am 

It is important to note that the frequency filter does not look across columns even if the attributes are related. For example, there are multiple formats for timestamps. The filter will not compare timestamps with different formats even if they are the exact same time.
