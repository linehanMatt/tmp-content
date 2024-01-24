---
title: 'S3 Connector App and Checkout Settings'
description: 'Learn how to set up data deliveries straight to your AWS account''s S3 bucket.  '
lastUpdated: '2022-05-12T19:11:08.804Z'
tags: ['Data Egress Through Connector Apps', 'Overview']
---
New to Outbound Connectors? Learn about the concept more generally: [What are Narrative Outbound Connectors](https://kb.narrative.io/what-is-a-narrative-outbound-connector) 

### Overview

AWS S3 is a popular way for Narrative users to store their datasets. The S3 App and Checkout Settings allow Narrative buyers to push data subscriptions directly to their AWS's S3 bucket in a fast and intuitive manner. Once a bucket is set up, buyers may access it for any Data Stream Marketplace or Buyer Studio subscription.

Users must have their own AWS account to receive subscriptions via the S3 Connector. You can create an account [here](https://aws.amazon.com/pm/serv-s3/?trk=fecf68c9-3874-4ae2-a7ed-72b6d19c8034&sc_channel=ps&sc_campaign=acquisition&sc_medium=ACQ-P|PS-GO|Brand|Desktop|SU|Storage|S3|US|EN|Text&s_kwcid=AL!4422!3!488982706710!p!!g!!amazon%20s3%20account&ef_id=Cj0KCQjw4PKTBhD8ARIsAHChzRLobwTN-0URXY5Rt3vl4UpP2B0_uCA92enmL1SxIZX6Ff-s9rLmJvYaArGpEALw_wcB:G:s&s_kwcid=AL!4422!3!488982706710!p!!g!!amazon%20s3%20account) if you do not already have one. 

### Installing S3 Connector App 

The S3 Connector App is located within the [apps tab](https://app.narrative.io/apps) on Narrative's website. You can install the app by logging into your Narrative profile and clicking the install button on the app's tile card. If the install button does not appear or the install request times out, please contact support@narrative.io.  

### Setting Up Bucket Profiles 

Once you launch Narrative's S3 Connector App, select the Connector Settings tab located on the left side. This screen will prompt you to create a new profile with the blue New Profile button in the upper righthand corner. Click the New Profile button to begin linking your S3 bucket to Narrative's system. 

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-17%20at%2012-44-07%20PM-png.png)

#### New AWS Profile 

The New Profile button should guide users to the New AWS Profile screen where they can configure their profile name, profile description, and bucket name. Please have a separate screen up with the S3 bucket you intend to use for Narrative's S3 Connector. 

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-17%20at%2012-53-10%20PM-png.png)

**Profile Name:** Add a descriptive name to identify your bucket during profile management and subscription checkout. For example, "North American Location Data" provides enough information to distinguish this bucket's use case while still leaving the name open ended enough to include multiple subscriptions.    

**Description:** Describe the the reasons why you or someone in your company would use this bucket. These indicators will help your team distinguish between different profile use cases.  

**Bucket Name:** Indicate the bucket within your AWS S3 account that should receive your data subscriptions. For example, a Narrative S3 bucket may look something like s3://narrative-testing-bucket. Users should copy and paste "narrative-testing-bucket" into the Bucket Name text box. Subdirectories for each data delivery can be created during a subscription's checkout process.   

Continue to the next section once you have entered your profile name, profile description, and bucket name.  

#### Giving Narrative Access to Deliver Your Subscription Files

You are now ready to add a new Bucket Policy and a Bucket Tag to your S3 bucket. Narrative requires users to add a policy to their AWS bucket to ensure that Narrative can successfully deliver data. To add the new policy, copy the policy Narrative provides you on the Configure S3 Bucket Page, then navigate to your bucket in the AWS console. 

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-17%20at%201-08-56%20PM-png.png)

Once you have opened your bucket, click on Permissions tab and then under the Bucket Policy section, click Edit. Delete the bucket's current policy and paste the policy you just copied above. Your policy should now look very close to the image below.

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-17%20at%201-12-26%20PM-png.png)

Click Save and return to the Configure S3 Bucket page. As a final verification step, Narrative also requires you to add a tag to your AWS bucket. This ensures that you are the owner of the bucket. Copy the Tag Key that Narrative provides you on the Configure S3 Bucket Page.

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-17%20at%201-27-20%20PM-png.png)

To add the tag, navigate to your bucket in the AWS console. Click on Properties and under the Tags section, click Edit. If your bucket already has a tag, make sure to select Add tag instead of replacing the tag you already have. Paste the Tag Key in the Key text box and then repeat the same copy and paste process for the Key Value. Both are required for Narrative to ensure the connector is set up properly.  

 ![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-17%20at%201-28-51%20PM-png.png)

Click Save and return to the Narrative's Configure S3 Bucket page to test your bucket's connection. Click the Test Connection button and you should receive a green message letting you know that the bucket was set up correctly. If you get a red error message, repeat the bucket policy and bucket tag steps and test again. If the issue persists, please reach out to support@narrative.io for assistance. 

The final step to create your S3 Connector is to select your output file type and configuration. You can choose either CSV, TSV, JSON and Parquet as your output. Users who select JSON or Parquet do not have to specify any extra configurations for their file while users who want CSV and TSV must choose a delimiter, escape character, header, and quote. See the image below for more details on CSV and TSV configurations. 

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202022-05-12%20at%209-35-02%20AM-png.png)

Click the Save And Finish button to begin using your profile for subscription deliveries. 

### Adding Your S3 Destination During Checkout 

You are ready to use a S3 Connector profile in your Buyer Studio or Data Streams Marketplace subscription. During the destination step, toggle on the S3 connector and select the profile that should receive the subscription's data deliveries. 

### ![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-17%20at%202-25-33%20PM-png.png)

You may also create a subdirectory within your bucket to better organize your data deliveries. For example, a subscription that sends location data could have a subdirectory of "LocationData" to better organize all the subscriptions going to this bucket. Bucket prefixes may not have spaces in the name. 

Narrative will automatically create the subdirectory with the name you input for Bucket Prefix. There is no need for you to show the directory's path such as "TestProfile/LocationData". 

It is easy to send this subscription to multiple buckets by selecting "Add An Additional Profile" and choosing the second profile. Users can create distinct bucket prefixes for each additional profile. 

![](https://solutions.narrative.io/hubfs/Screen%20Shot%202021-12-17%20at%203-14-26%20PM-png.png)

Click Save and Continue to finish the checkout process. You will now receive data deliveries in your specified S3 bucket! Please reach out to support@narrative.io with any questions.
