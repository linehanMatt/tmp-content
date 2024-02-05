---
title: Working with Large & Complex Datasets
description: My data is complex. I have tables with hundreds of columns and billions of rows.  Can Narrative's Platform still work for me?
type: ask-me-anything
additionalResources: []
---


::customer-interaction{title="Big Data"}
#customer
My data is very large.  We create over a terabyte of data every day and including our historical data we are in the petabyte range.  Can your platform handle that?

#responder
Absolutely. Narrative's software was build to scale horizontally across petabyte scale datasets.  We have multiple customers who are ingesting and querying data at this scale today.

#cta
::item-grid{}
    ::feature-callout{title="Easy Data Ingestion" description="We've made data ingestion dead simple and scale is never an issue." link-path="/products/my-data/easy-dataset-ingestion" link-text="Learn more"}
    ::

    ::feature-callout{title="Queries At Any Scale" description="We've made data ingestion dead simple and scale is never an issue." link-path="/products/query-builder" link-text="Learn more"}
    ::
::
::

::customer-interaction{title="Hundreds of Fields"}
#customer
Some of my tables have hundreds of columns. Some even have thousands.  Can your platform handle that?

#responder
Yes.  Narrative's platform is designed to handle the most complex data schemas, making it easy to ingest and use data no matter your use case or data source.

Our AI data normalization service Rosetta Stone will even map all of your columns to a standard set of attributes making it easy for you and your partners to ignore the complexity of the underlying structure of your data and focus on what they are looking for.

#cta
::feature-callout{title="Rosetta Stone" description="Narrative has created an AI model called Rosetta Stone to auomatically normalize data as it flows into the platform." link-path="/products/rosetta-stone" link-text="Learn more"}
::
::

::customer-interaction{title="Types of Data"}
#customer
My data isn't just numbers and strings. Can you handle more complex data types?

#responder
Of course.  Data managed by Narrative can include strings, numbers, timestamps, boolean values, and even complex data types like array and objects (structs).  We even have the ability to handle spacial data structures like polygons and points.

Today we do not directly support binary data (images, videos, etc.) but we can store pointers to binary data in the form of a string and any metadata associated with the binary data can be stored in one of the previously mentioned data types.

#cta
::feature-callout{title="Your Data, Your Schema" description="Narrative has created an AI model called Rosetta Stone to auomatically normalize data as it flows into the platform." link-path="/products/my-data/flexible-schemas" link-text="Learn more"}
::
::

::customer-interaction{title="Will Queries be Slow?"}
#customer
If I have data at this scale will my queries always be slow?

#responder
Absolutely not.  There are a number of features we've built out to provide fast query times to our users:

- **Configurable Compute**: You can scale up the compute resources for your queries to ensure they run as fast as possible.
- **Only Read the Data You Need**: If you have hundreds of columns, but are only querying a few of them, our platform will only read the nessecary data.
- **Indexes / Partitioning**: We offer a number of features to ensure that your data is organized in a way that makes querying fast including partitioning data by commonly filtered fields.
- **Sampled Forcasting**: If you are running a query that is going to take a long time, we can run it on a sample of the data to give you a quick answer and then run it on the full dataset if you are happy with the results.

#cta
::item-grid{}
    ::feature-callout{title="Query Builder" description="Narrative offers an intuitive WYSIWYG query builder to make collaborating easy" link-path="/products/query-builder/wysiwyg-editor" link-text="Learn more"}
    ::

    ::feature-callout{title="Narrative Query Language" description="NQL is a powerful SQL extension that makes it easy to express complex data requests." link-path="/products/query-builder/nql" link-text="Learn more"}
    ::

    ::feature-callout{title="Fast & Accurate Forecasting" description="Get insights from your data without waiting an eternity" link-path="/products/query-builder/fast-and-accurate-forecasting" link-text="Learn more"}
    ::
::
::

::customer-interaction{title="User Experience"}
#customer
Surely the user experience must be terrible with data at this scale and complexity?

#responder
Not at all.  We build query builder -- our WYSIWYG query builder -- to make it easy to express complex data requests.  We also offer a powerful SQL extension called the Narrative Query Language (NQL) that makes it easy to express complex data requests.

We also offer help in the form of Rosetta, our AI digitial assistant.  She can help you write the toughest queries and solve the stickiest problems even if you aren't a data savant.

#cta
::item-grid{}
    ::feature-callout{title="Query Builder" description="Our WYSIWYG way to construct queries on top of complex datasets." link-path="/products/query-builder" link-text="Learn more"}
    ::

    ::feature-callout{title="Digital Assistant" description="Rosetta, our digital assistant, can help you with your gnarliest projects.  Just ask her." link-path="/products/rosetta" link-text="Learn more"}
    ::
::
::

::customer-interaction{title="Next Steps"}
#customer
Color me impressed. How do I get started?

#responder
We'd be happy to set up a demo tailored to your specific use case and discuss how our platform can meet your needs. Following the demo, we can explore integration options and start the onboarding process to ensure you have access to the data and tools necessary for your audience building initiatives.

#cta
::mega-feature-callout{title="Get Started" subtitle="Let's Get You Building" description="We'd be happy to set up a demo tailored to your specific use case and discuss how our platform can meet your needs." link-url="/contact" link-text="Contact Us"}
::
::
