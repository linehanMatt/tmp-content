---
title: 'What are the costs associated with acquiring data through Buyer Studio?'
description: 'This article will explain Buyer Studio''s Marketplace Data Costs, Marketplace Data Transaction Fee, and Platform Processing Costs.'
lastUpdated: '2023-03-22T12:39:25.804Z'
tags: ['Buying Data', 'Costs ']
---
### **Costs Overview:** 

Buyer Studio is a data acquisition product designed to assist buyers in acquiring high-quality data in large quantities. In this article, we’ll walk you through the costs and fees associated with activating a Buyer Studio one time order or subscription: 

**Marketplace Data Costs:** the value to be paid by the buyer to the data provider for licensing their data.

**Marketplace Data Transaction Fee:** the value to be paid by the buyer to Narrative, charged as a percentage of the marketplace data costs_._

**Platform Processing Costs:** the value to be paid by the buyer to Narrative for the compute resources required to run a subscription, charged as a dollars-per-byte fee. 

Narrative uses data and cost forecasts to estimate a user's marketplace data costs, marketplace data transaction fee, and platform processing costs before activating an order. Note that there may also be transfer and storage costs associated with the order, depending on where the data is sent. 

### Costs In Buyer Studio's Workflow

#### **Automatic Forecasting** 

Buyer Studio's cost inputs are pulled from Narrative's data forecasting feature. Once the user completes the Providers section and proceeds to the Destination section, a forecast looking at the cost and available rows automatically starts in the "Data Forecast" widget found at the top of the UI. 

Narrative recommends that users wait for the forecast to return results before entering a budget or activating the subscription.

#### Costs Screen

Buyer Studio shows the monetary costs of activating a subscription once the forecast is finished. Once a user enters their budget, every display that requires a forecast to come back should have a spinning wheel indicating that Narrative is calculating the results. **The platform processing costs are in addition to the budget a user enters for their marketplace data costs and marketplace data transaction fee. The entered budget does not account for a user's processing costs**. For example, if a user adds a budget of $10,000, and the forecast returns with a $5,000 cost for processing, the price of activating the subscription (without any transfer or storage) is $15,000. Users who want to learn about lowering their subscription processing rate should contact Narrative.

Once the cost forecast comes back, the user should be able to see the data processing cost and cost of deliverable data under the "Budget and Delivery Cadence" section. A buyer's budget does take into account their marketplace data transaction fee, meaning if their budget is $100, and their transaction fee is 25%, Narrative will transact $80 of data (price before marketplace fees) and charge them $100 (1.25 \* $80 = $100).

If the cost forecast does not return before the user activates their subscription, no marketplace data cost or transaction fee are displayed. **There is no blocker preventing a user from creating a subscription without seeing the results of their forecast.**

![](https://solutions.narrative.io/hubfs/Screenshot%202023-03-14%20at%205-05-34%20PM-png-1.png)
