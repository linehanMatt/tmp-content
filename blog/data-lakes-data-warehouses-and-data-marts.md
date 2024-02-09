---
title: 'Data Storage 101: Data Lakes, Data Warehouses, and Data Marts'
description: 'Data lakes, data warehouses, and data marts are all used for storing big data, but they are not interchangeable terms. This crash course on data storage will lay out the definitions and differentiators for these key terms.'
publishDate: '2021-10-20 17:19:24'
author: 'Brenna Dilger'
ogImage: '/img/blog/2021/10/lake-vs-warehouse.png'
image: '/img/blog/2021/10/lake-vs-warehouse.png'
tags: ['data science']

---
In the world of big data, it is important to find ways to store the overwhelming volumes of data that are being generated every second. Data professionals have found that it is generally useful to either pour their data into data lakes or stack their data into data warehouses (and data mart subdivisions). This crash course on data storage will lay out the definitions and differentiators of these data storage solutions and explain their unique functions.

## What is a data lake?

A data lake is a repository of raw data that has been stored in its native format. Much like a normal lake can be dipped into in order to retrieve unfiltered and unprocessed water, a data lake can be dipped into in order to access data that has not been processed or analyzed. It is a body of data in its purest form.

James Dixon, founder and former CTO of Pentaho, has been credited with coining the term “data lake” and created an analogy to explain his concept that perfectly fits the term:

“The Data Lake is a large body of water in a more natural state. The contents of the Data Lake stream in from a source to fill the lake, and various users of the lake can come to examine, dive in, or take samples.”

## So what are data marts and data warehouses?

Data marts are archives of normally structured and stored data. In Dixon’s analogy, he likens a data mart to “a store of bottled water, cleansed and packaged and structured for easy consumption.” Data marts are generally used and managed by a specific community or department and are often a subdivision of a data warehouse.

Data warehouses are bigger storage locations that store archived and ordered data from a wide range of sources. Data is packaged and organized just like stored goods would be in a manufacturer's warehouse.

## What are the main differences between data lakes and data warehouses?

The most important distinction between a data lake and a data warehouse is that data flows into a data lake in its absolute raw, native form while data arrives at a data warehouse in a structured and defined form.

## Data lakes retain all data and support all data types

Data lakes want all data to feel welcome. Any and all data is allowed to swim in a data lake. Data warehouses, however, are like high-profile data nightclubs; they only let in the data they decide is worthy of being there.

Data lakes retain data that is useful, data that isn’t useful, data that will be used immediately, and data that may never be used at all. No data is left behind. It is poured into the lake without planning or structure. Data lakes also support all types of data: structured, semi-structured and unstructured data. All of the data in a data lake is kept in its native format and will only be transformed if it is ready to be used.

A data warehouse is more discriminatory; it only includes data that has been structured and that has an identified use. When a data warehouse is developed, a significant amount of time is spent analyzing the data that will be stored within it. Decisions are made regarding what data will or won’t make the cut: if the data is useful, it will be included in the data warehouse and if the data is not useful, it will be excluded.

## Data lakes adapt easily to changes and provide faster insights

One of the major disadvantages of data warehouses is how long it takes to change them. Because of the complexity of the data warehouse’s structure, making changes to these models is a tedious and lengthy process.

Data lakes are much more flexible since they don’t have a defined structure at all. They are free-flowing data reservoirs that can be configured and reconfigured as needed. The data is explorable in a way that can answer more questions and gain more insight. Because data lakes contain all data, support all data types, and enable access to data before it has been transformed and structured, they are also able to provide faster results than the traditional data warehouse approach.

## How should data lakes and data warehouses be used?

Data lakes and data warehouses are different tools that serve different purposes. Data warehouses are often used as a way of sharing data and content across a specific team or department in an organized and efficient way. Data lakes, on the other hand, are used and accessed by anyone that needs raw data. The data within data lakes has the capability to be analyzed and transformed in any organization, department, or team that might make use of it.

If your organization has an established data warehouse, it might be a good idea to implement a data lake alongside it to remove some of the constraints that a data warehouse may be placing on the potential of your data.

## Narrative’s data lake is vast, transparent, and swimming with data

One of our foundations at Narrative is our commitment to [always keep data raw](/blog/the-narrative-manifesto-part-two), never modeled or transformed. We aim to maximize the potential of all data’s specificity and usefulness. That’s why we use a data lake to store our buyer’s and seller’s data. The data lake model adapts and scales easily for large volumes of data and it can handle any data type or structure. The ease of feeding data into our data lake empowers data distributors to monetize large quantities of natively stored data while the flexibility of accessing the data in our data lake allows data buyers to explore and transform data in its purest form.

**Narrative makes it easy to buy and sell raw data.**

[**Schedule some time with our experts**](/contact) **to learn more!
