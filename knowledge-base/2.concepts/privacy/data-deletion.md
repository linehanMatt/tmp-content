---
title: 'How Does Narrative Make Sure Buyers Follow Data Licenses'
description: 'Review Narrative''s data purge policy and how seller data is protected from misuse. '
lastUpdated: '2023-06-14T18:07:20.838Z'
tags: ['Selling Data', 'Narrative Data Policies']
---
### Overview

In an effort to do our part in making sure buyers follow the set data licensing periods via Narrative, we have a data purge feature which removes delivered data a specific amount of days after delivery. Any data that is used beyond that date is in direct violation of our contractual agreement and will result in an automatic cancelation of service.

### **What**

Purchased data is no longer accessible once the license period has ended, which is usually 30 days if the buyer is using Narrative's standard purchase agreement. The buyer is obligated to cease all operations that use expired data if they have removed it from a Narrative controlled S3 bucket.

### **Why**

This helps make sure your data deliveries are used within their appropriate license periods.

### **How**

For example, a file delivered to a bucket on November 3rd will automatically be purged on December 3rd. This is not related to the supplier timestamp (the date the observation was collected), but rather the date Narrative _delivered the file_.

Specifically:

> * Anything older than **30 days** will be automatically deleted from buyer buckets

Please don't hesitate to reach out with any questions or concerns about this policy.
