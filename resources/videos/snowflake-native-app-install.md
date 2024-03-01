---
title: Installing the Narrative Snowflake Native App
videoId: 4b0bf64a148529c21be5cee671d3d06b
description: A quick video showing how to install and configure our Snowflake Native App
type: video
---
Today we are going to install the Snowflake Native App 'Narrative Data Collaboration powered by Rosetta stone into my Snowflake account.  

The goal of this native app is to allow you to use the powerful AI data collaboration tools provided by the Narrative platform in your Snowflake data plane. 

<!--more-->


Meaning you can interact with your data through the Narrative platform UI, query your data, and even deliver your data to Narrative connector framework destinations, such as Facebook or The Trade Desk. All without your data, leaving your Snowflake account and with all of the processing happening within your Snowflake instance. Now a prerequisite to performing this installation is that you must be an account admin or have equivalent privileges in your Snowflake account. Another prerequisite is that you must have created an account at app.Narrative.io/platform/ so that you can generate your API key and hook your data and your Snowflake account up to the Narrative platform. 

   Let's get started. Step one is to set up an external access integration from your Snowflake account that allows your Snowflake account to access our application api (api.Narrative.io). And in order to do this, you're going to need to copy and paste two separate commands into a Snowflake worksheet. 

So I'm going to copy the first command . 

Switch over to a Snowflake worksheet. Open up SQL worksheet, paste  k the command and run. As you can see this command has run successfully. I'm going to now run the second command. 

 And again, this statement has run . 

I'm going to click this  check box, showing that an administrator has created the required external access integration, and I'm going to complete initialization. 

 Onto step two.  Step two navigate to the Narrative platform UI and create a long lived access token. This is an access token that I'll insert into my Snowflake account that will allow me to interact with the Narrative platform.  Flipping over to the narrow platform UI I'm coming down to settings, API keys. I'm going to create a new API key. I'm going to give it a name.. I'm gonna leave it at the default expiration, which is a year from now. And I'm going to select the permissions that were described in the app. 

 Read and write data planes. Read and write data sets. And read and write jobs.. And now I have a new API token. This API token  will not be displayed again, so you need to copy it and paste it somewhere safe.  

. I have navigate back to the app install, screen. I insert my app token.  Click save.  Onto the next step. Now it's time to set up the compute warehouse, please select the warehouse in which Narrative data collaboration will run when executing queries. 

My case, I'm going to grab our test warehouse and click save.

 Next step. In order to query data and deliver it to end points on my behalf, Narrative data collaboration requires the execute task privilege. This is as simple as opening grant privileges. You're granted the privilege to the app. 



 Now I need to select which table is going to be used as a dataset within the Narrative platform. 

First I'm going to give it a name. We're going to call this sports merchandise. Purchase history. 

And we're going to configure a source table.

I'm in here. It's like sports sales. 

And click save.  Now I'm going to be asked to upload a sample of the source table to Narrative. This is an optional step, but it is required for Rosetta stone optimizations and AI automations . So we're going to upload a sample dataset.  And a uniform random sample of the dataset of a thousand rows is selected for me and uploads to the Narrative platform.

And finally, I'm going to come in and select the polling. Frequency Narrative checks for new jobs.  I have now completed the install of the Snowflake Native App 

and I am now able to begin interacting with my data within the Narrative platform.