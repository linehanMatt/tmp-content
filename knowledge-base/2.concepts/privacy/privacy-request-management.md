---
title: 'Narrative Data Privacy Request Management'
description: 'Narrative''s Data Collaboration Platform offers a comprehensive solution to help you manage your obligations as a data controller and data owner under GDPR and various other data policy regimes.'
lastUpdated: '2023-10-31T20:44:04.903Z'
tags: ['Legal / Compliance / Privacy', 'Regulations & Compliance']
---

#### **Introduction**

Narrative's Data Collaboration Platform offers a comprehensive solution to help you manage your obligations as a data controller and data owner under various privacy regimes. Our Privacy Request Management Product is designed to simplify the process of adhering to data subjects requests, ensuring compliance with GDPR and other privacy legislations. This article will give you an overview of the tools and processes that Narrative puts at your disposal.

#### **What is a Data Privacy Request?**

A data privacy request, sometimes referred to as a Data Subject Request (DSR), is a formal request from a data subject exercising their rights under various privacy laws, such as the General Data Protection Regulation (GDPR). These requests can include _opt-out requests_, where the data subject asks to be removed from marketing communications or targeted advertising, and _the right to be deleted requests_, where the data subject requests the complete erasure of their personal data.

#### **Narrative's Role as a Data Processor**

As a data processor, Narrative assists data controllers in processing and complying with  data subjects' privacy requests under various privacy laws, including GDPR and CCPA. We support all privacy regimes through a single product solution, making it simple for you to pass privacy requests to downstream data collaborators.

#### **How Privacy Request Management Works**

### **For Data Owners**

As a data owner, regulatory frameworks like CCPA and GDPR hold you responsible for complying with privacy requests you receive from data subjects. When you receive a privacy request, follow these steps to pass the request along to your downstream data collaborators:

Data Privacy requests can be sent to Narrative’s Data Collaboration Platform via the following methodologies:

1. Update the dataset in your account titled "Privacy Request Identifier Dataset" by appending a row of data containing the identifier of the data subject and the specific type of request you have received.
2. Create a new dataset and map it to the Rosetta Stone Attribute "Data Privacy Request Identifier" (ID 232).
3. For optimal data management and compliance, set a 30-day Retention Policy on datasets containing PII identifiers subject to opt-out or privacy requests. This approach promotes timely data deletion, aligning with many privacy guidelines. Always tailor your policy to the specific regulations of your jurisdiction, such as GDPR or CCPA.

When Narrative receives privacy requests, the platform will automatically take the following actions on your behalf:

1. We prevent the data subject's information from being transacted on after receiving the privacy request. No party will be able to query, receive, or filter on this value if the identifier is provided.
2. We pass the identifier downstream to any consumer that has transacted on your data, allowing them to comply with the privacy request wherever they have already exfiltrated this data.

### **For Data Buyers**

Whenever you subscribe to data containing user identifiers, we will automatically subscribe you to receive all relevant privacy requests that have been passed to Narrative from suppliers that you have purchased data from. These requests will appear in My Data under Purchased Data. It is your responsibility to comply with a data privacy request when it is passed along to you, in cases where you have already purchased and exfiltrated data that matches the identifier related to the privacy request.

#### **Data Privacy Request Identifier Attribute**

The Data Privacy Request Identifier Attribute expects two values in your data privacy dataset:

1. **Identifier**: Any unique identifier, such as hashed email, mobile advertising ID (MAID), or cookie. Any identifier will work.
2. **Request Type**: One of the following:
    * "opt\_out"
    * "data\_erasure"

By following these guidelines, you can ensure that your compliance with data subjects' privacy requests is simple and easy using Narrative's Data Collaboration Platform.
