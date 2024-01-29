---
title: 'What is an Attribute?'
description: 'Learn about the building blocks that make up any Narrative transaction.  '
lastUpdated: '2021-12-08T14:41:57.935Z'
tags: ['Welcome to Narrative', 'FAQs']
---
**Attribute**: A data characteristic that is standardized and made available by Narrative for transactions. Attributes are combined to create multi-provider data streams, which can be purchased in subscriptions.
  
An attribute consists of:  
\- Name  
\- Description  
\- Tags  
\- Validations  
\- Type (including types of contained fields)  
  
If the type is object, the attribute will contain fields that are primitive types or that reference other attributes. For example, the Unique Identifier attribute is made up of a type, value, and context. The type is a string that categorizes each ID, the value is a seemingly random combination of letters and numbers, and the context is the high level, human readable category that the ID falls under.

#### Why do Attributes matter?

Attributes become the translator between the way a seller expresses a data point and the way a buyer sees it in Narrative's platform. Narrative translates and normalizes the column so buyers no longer have to worry about an out of bounds data point breaking their system. It also helps aggregate data that would otherwise seem distinct. For example one seller may send over gender data as "male"/"female" and another may send "m"/"f." Narrative's Rosetta Stone makes sure this difference does not affect your data delivery.
