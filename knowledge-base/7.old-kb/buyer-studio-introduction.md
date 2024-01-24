---
title: 'How do I get Started With Narrative''s Buyer Studio App'
description: 'Learn how to use the world''s most customizable and efficient data purchasing tool.  '
lastUpdated: '2023-03-21T16:34:11.580Z'
tags: ['Buying Data', 'Buyer Studio']
---
### Overview 

Accessing different providers' data has historically been a complex and tedious process. Learning one provider's schema does not necessarily translate to another's, creating an unscalable process that wastes both time and money. Buyer Studio aims to solve these headaches through a simple app that allows users to truly customize their data purchases. Want to set up a quick subscription to target males that use food delivery apps? Buyer Studio allows you to set up this order within minutes. How about women in Urbandale, Iowa who have a birthday in March? Buyer Studio gives you a myriad of filters to prevent you from paying for irrelevant data. 

Check out Buyer Studio's [more info page](https://app.narrative.io/app/buyer-studio) to learn about the app's benefits and pricing. This article will provide a step by step guide on how to create a data subscription using Buyer Studio.  

#### Installing Buyer Studio  

The Buyer Studio App is located within the [apps tab](https://app.narrative.io/apps) on Narrative's website. Users may install the app by logging into their Narrative profile and clicking the install button on the app's tile card. If the install button does not appear or the install request times out, please contact support@narrative.io for assistance.  

### Creating A Subscription 

Now that the app is installed, you are ready to set up your first data order. Data orders are available through Narrative's subscription format and will remain active until the order is turned off. To get started, press the New Subscription button located on the left side navigation bar. 

![Screen Shot 2021-12-07 at 4.14.08 PM](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-07%20at%204.14.08%20PM.png)

This article will just cover orders placed through the New Subscription button. To learn about other ways to set up subscriptions in Buyer Studio check out [Schema Presets](https://kb.narrative.io/buyer-studio-presets?hs_preview=mzQwSzjz-61403071022)  

#### Select Attributes

After pressing the New Subscription button you should be brought to the Select Attributes page. Here you will create the [foundation of your data order](https://kb.narrative.io/what-is-an-attribute). On this page you will choose all the attributes that you want in your subscription. Each attribute comes with two toggle options: Deliverable and Filterable

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-08%20at%2010-05-17%20AM-png.png)

**Deliverable**: The selected attribute will be a part of your pending dataset. Each attribute may come with sub attributes that automatically become deliverable and filterable once you toggle on the main attribute. Each sub attribute comes with its own set of toggles that provide the same functionality. 

**Filterable:** The selected attribute will be a filter for your dataset. Turning off filterable means you will not have access to this attribute in the filter section and the attribute will only show up in your subscription when it's available. 

It is important to note that these toggles are not reliant on one another. Our system defaults to deliverable AND filterable when an attribute is selected, but you may just want filterable or deliverable. 

**Example Order:** In the order above, I selected Unique Identifier as deliverable and filterable. This means that I want to receive Unique Identifiers in my order, but only when it meets my filter specifications. I will create these filters during the next step. Once I toggle on deliverable, all of Unique Identifier's sub attributes (type, value, and context) automatically toggled on as well. I expanded the Unique Identifier attribute by clicking on its designated rectangle and toggled off the context sub attribute as it was not important for my use case.

I also want the Event Timestamp attribute in my order and plan on creating a specified date range through this attribute's properties in the filter section. Event Timestamp has no sub attributes. Lastly, I want to determine the country in which my Unique Identifiers came from through the Country Code attribute. I will select this attribute as filterable but not deliverable. I want to filter the countries that my data will come from, but do not want to receive their country code in my order.     

Narrative offers multiple pages of attributes to select from. Press the blue Continue button once you have selected all of the attributes you want in your order. 

#### Add Filters

You have now selected all your attributes and are ready to filter them to your exact specifications. But before you filter each attribute, you must set a Price Ceiling for your order. 

**Price Ceiling**: The maximum price you are willing to spend per 1,000 data points. A higher Price Ceiling considers more attribute for inclusion in your order. You may change the price by entering a number in the specified text box or by using the slider. 

In my order, I selected a Price Ceiling of $10. Once you have selected your price, you are ready to begin filtering your attributes. Each attribute comes with three filter options: Include all values, Include if present, and Custom.

**Include all values:** Includes a row of data whether or not the value is present. 

**Include if present:** Includes a row of data if the attribute is present. 

**Custom:** This filter specifies a set of criteria that the value must meet in order for the row to be included in your dataset. The format of the custom filter depends on the selected attribute. For example, the Event Timestamp's custom filter is a date range created in a calendar while the Country Code custom filter is a dropdown of every country in Narrative's system. 

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-08%20at%2011-00-20%20AM-png.png)

For my order, I want to filter the Unique Identifier's type to only include ADID (Google phones) and IDFA (Apple phones). I selected these types through the Custom filter's dropdown menu. I do not want to filter on the Unique Identifier's value so I will leave that filter's settings on Include all values. 

![Screen Shot 2021-12-08 at 11.08.38 AM](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-08%20at%2011.08.38%20AM.png)

For the Event Timestamp filter I want to include any value that was found between November 2nd, 2021 and January fifth, 2022. I am allowed to select future dates since the subscription will automatically continue to run until canceled. 

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-08%20at%2011-16-21%20AM-png.png)

I also want a custom Country Code filter that includes values in the US, Canada, and Mexico. As a reminder, I will not receive this attribute because I did not mark it as deliverable. I will therefore not know which rows of data belong to a Unique Identifier located in the US, Canada, and Mexico. However, I will know that any row of data that I receive must have been found in one of those three countries.  

After attribute filters, the user must decide on a Deduplication Strategy and Frequency Filter. 

**Deduplication Strategy**: This filter determines whether or not you would like to receive the same data point more than once. By default an order will not deduplicate any data points. [Use this link](https://kb.narrative.io/duplicate-data) to learn more about Deduplication Strategy.  

**Frequency Filter:** This filter creates a minimum and/or maximum range for the amount of times the specific data point must show up in that dataset's column. By default an order will not have a Frequency Filter. [Use this link](https://kb.narrative.io/buyer-studio-frequency-filter) to learn more about Frequency Filters. 

Frequency filtering and deduplication can be used together in the same subscription. However, frequency filtering occurs after deduplication i.e. frequency filtering happens on the result of deduplication. If two rows are considered duplicates and there is a Deduplication Strategy, the Frequency Filter will only receive one row to filter. 

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-08%20at%203-50-32%20PM-png.png)

In my order I want a deduplication strategy to filter out all the duplicate Unique Identifier values i.e. I only want to see a specific Google Phone or Apple Phone Once in a single delivery. I will buy this data point once every 30 days to make sure the device is still in North America. I do not want a Frequency Filter on this order. 

Click Continue to move on to the providers filter section. 

#### Providers

Buyer Studio also offers the option to filter by specific providers through the Custom button. If you would like to work with a select few suppliers, press the include option and then choose your providers from the dropdown. You can also select certain providers that you do not want to work with through the exclude option.

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-08%20at%2011-26-14%20AM-png.png)

I will not filter by provider since I want to receive all the data possible that meets my filter criteria. I will instead choose the Buy from all sellers button.  

#### Destination 

Narrative offers the ability to send data outside the platform through Narrative Outbound Connectors. [Use this link](https://kb.narrative.io/what-is-a-narrative-outbound-connector) to learn more about Outbound Connectors. For now I will select Download from Narrative and receive my subscription's delivery under Narrative's subscriptions page in the top right corner of the website.  

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-09%20at%209-41-12%20AM-png.png)

#### **Budget**

Now we will select a budget and delivery cadence for your subscription. 

**Subscription Cadence**:  Subscription Cadence supports one time, hourly, daily, weekly, and monthly data deliveries into your specified destination. [Use this link](https://kb.narrative.io/buyer-studio-subscription-cadence) to learn more about Subscription Cadences. 

**Budget:** Budgets are set up on a monthly cycle. You will receive data deliveries on your specified cadence until your budget for the month is used up. 

Budgets reset at the start of the month regardless of when the order was created. 

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-08%20at%204-35-58%20PM-png.png)

I will set my delivery cadence to weekly and receive downloadable files every Sunday morning throughout the month until my $1000 budget is maxed out. The orders will then resume at the start of the next month. 

#### Payment 

Buyer Studio currently only accepts credit cards as your subscription's payment method. Click Update Payment Method to add a credit card to your file. Once you are done, click Save Settings and you will be brought back to your Buyer Studio order. I am going to use the credit card already associated with my account. 

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-09%20at%2010-31-02%20AM-png.png)

#### Confirmation 

You are finally ready to activate your subscription! Please enter a descriptive Subscription Name and Subscription Description. You may want to touch on the attributes you bought and the purpose of the order. For name I entered: "North America MAID Campaign" and description: "Event Timestamp from November 2021 to January 2022 - Google and Apple Phones"

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-09%20at%2010-51-06%20AM-png.png)

**Order Summary**: Let's review the order I just created. In the attribute section I selected Unique Identifier, Event Timestamp, and Country Code. These attributes became the building blocks of my order. During the filter step I added Unique Identifier types of ADID and IDFA, which represent Google and Apple Phones, filtered Event Timestamp down to a two month window, and made sure any of the devices I receive came from North America using the Country Code filter. I did not want duplicate ADID and IDFA values so I filtered them out using the Deduplication Strategy filter. I then selected to download this subscription from Narrative on a weekly cadence with a monthly budget of $1,000. After selecting my credit card I was ready to activate my subscription and start receiving data!  

Please reach out to support@narrative.io with any Buyer Studio questions.
