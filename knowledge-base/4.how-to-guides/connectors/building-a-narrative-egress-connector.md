---
title: 'Building a Narrative Egress Connector Native App'
description: 'Building a Narrative Egress Connector Native App adds new functionality and destinations for the data that is purchased or shared within the Narrative platform. '
lastUpdated: '2022-11-01T13:01:55.816Z'
tags: ['Integrations & Technical Guides', 'Destinations']
---
Building a Narrative Egress Connector Native App adds new functionality and destinations for the data that is purchased or shared within the Narrative platform. To get started, reach out to your account manager to set up a meeting with our team.

### **What are the goals of an egress connector app?**

Egress Connector Apps help Narrative users to deliver data from the Narrative platform to a destination outside of the platform. Some examples of destinations that a connector can deliver to include an AWS S3 bucket, an SFTP location, or a Facebook Ads Manager account.

You can read more about the user experience governing an egress connector app on our [Knowledge Base here](https://kb.narrative.io/what-is-a-narrative-outbound-connector).

### Advantages of the Narrative Native App Platform

Building a Narrative connector app is generally very straightforward. In addition, our architecture has a few advantages meant to keep the developer experience simple and speed time to market for your app. In particular:

* Narrative gives developers a single app token to use to manage deliveries (no need to have a user-specific token for each user you interact with.)
* Narrative keeps track of the state of data deliveries for you; you only need to track which deliveries your app has already made, and which need to be made in the future.

### **Problems to be solved by Connector App**

In order to deliver data that has been generated in the Narrative platform, a connector must accomplish the following:

* **Host a User Interface:** The App’s UI will be loaded in an iFrame and exposed to users directly within the Narrative Native App platform UI.
* **Provide Narrative with an app manifest:** The app manifest will describe the URL of your UI, the permissions required by your app, configuration for the navigation and landing pages, and any associated pricing.
* **Store user-specific information in your App Profile:** Using permissions granted by the API as described in the app manifest, the Connector App will retrieve a profile ID from the Narrative API. Within your own database, store the profile ID along with information specific to a user’s destination required for the delivery (for instance secret keys or authentication tokens to authorize against the destination’s API).
* **Poll Narrative API for deliveries:** Using a token granted by the Narrative OAUTH workflow, poll the Narrative API for a list of data snapshots or “deliveries” that are ready for consumption by the app, along with a download URL location for each delivery.
* **Deliver data:** Perform the delivery of data to your destination in an asynchronous manner when new deliveries are found.

### Host your User Interface

#### **App UI**

The user interface you host will appear within the Narrative UI. It will be available within the app when the user launches your app. It will have two components:

* **Narrative Navigation**: All Narrative Native Apps share the Narrative navigation bar, which contains links to each page in your app as defined in your manifest (individual site page with a unique URL).
* **Developer-hosted iFrame**: This is where the content of your hosted app UI will appear when a user navigates to one of the pages you define.

![Screen Shot 2022-08-10 at 8.15.14 AM (1)](https://solutions.narrative.io/hubfs/Screen%20Shot%202022-08-10%20at%208.15.14%20AM%20(1).png)

#### **Connector App Workflow**

Connector apps are unique in that the workflow for delivering data within Narrative lives both within your app as well as within Narrative platform functionality. For egress connector apps in particular, the user interface will accomplish the following workflow:

1. When a user launches your app, Narrative will pass an app token that is scoped to the currently active user to your web server. This app token will have all of the permissions defined in your app manifest. Your app will then render in the Narrative iFrame.
2. One primary responsibility of this UI for connector apps is to collect the information required by the user to manage profiles (create, edit or delete) stored in a database on your infrastructure\*\*,\*\* scoped to the user’s company, which can be utilized to authenticate against your destination API and deliver data to it.
3. Users will then utilize the Narrative UI to perform actions that result in data being sent to the connector app for delivery. These actions occur **outside of your app** and can include:
    1. A user purchases a data product from the **Data Marketplace.** At the checkout step, the user selects the **connector** they wish to use to deliver their data. The user attaches a **profile** and an optional **quick-settings** object to describe how and where to write their data (see below).
    2. A user elects to have a **Dataset** delivered to a connector app destination. The user selects the **dataset** they wish to have delivered in **Dataset Manager**, and then selects the **connector** they wish to use to deliver their data.

### Provide Narrative with an App Manifest

The App Manifest provides the Narrative platform with the following information, which is required in order to render your app. You can see the full, up to date JSON schema required for an app [here](https://json-schemas.narrative.dev/v1/app_manifest_schema.json).

App Manifests provide, at a minimum:

* Base URLs for development and production sites where the app’s UI is hosted
* Path to each of the pages in the app, for the Narrative Nav to render
* Narrative API permissions that your app requests when users install the app. These are the Narrative API permissions your app can perform on the user’s behalf in order to function
* Developer information so that users know who they are interacting with when they install your app.

#### Narrative Connector App Type

The Narrative Connector App Manifest will have App type “Connector” which will cause your app to appear in the “Destinations” section of the Dataset Manager app, and within the checkout workflow in Buyer Studio App, the Data Marketplace, and elsewhere in the platform.

#### **Narrative Connector App API permissions:**

In order to get the full list of Narrative Connector App API permissions that your app will need, reach out to your Narrative account representative.

### Store user-specific information in your App Profile

You will create profiles for users using the Narrative API [Profiles service](https://api.narrative.dev/#tag/Profiles).

Profiles on Narrative are simply unique IDs which you can use to reference configuration data for an individual user within your own database. No actual user data or authentication data is stored in the Narrative platform, you are responsible for matching the profile by its ID to the configuration within your own platform.

Typical data stored in a profile would include:

* User ID and account or company information
* Account authentication information required to use your API
* Account information required to render your app correctly

#### **Profiles and Quick Settings**

❗Note: Please read below to understand the difference between Profiles vs Quick Settings

* **Profiles** should store data required to authenticate a user to your destination API. These profiles are shared by all users in a company and are not specific to an individual data subscription. Narrative will return a **profile\_id** to you whenever a delivery is ready, and you will look up the specific information related to that profile\_id in your own database.
* **Quick settings** should store data specific to an individual subscription, such as a folder name or a bucket prefix for data to be written to. Narrative will return an entire **quick\_settings JSON** object to you whenever a delivery is ready.
  * Quick settings can be 2 key/value pairs and they are defined in your Manifest file.
  * Quick settings are optional.

### Poll Narrative Deliveries API

Narrative notifies you that there is data to deliver for your Connector App by updating the [Narrative Deliveries API service](https://api.narrative.dev/#tag/Subscriptions/paths/~1data-shops~1subscriptions~1%7Bsubscription_id%7D~1deliveries/get).

For an example of the connector, you can look at the Narrative S3 Connector, which we have open sourced. See the [readme](https://github.com/narrative-io/narrative-s3-connector/tree/main/backend) here.

We recommend that you poll the Narrative Deliveries API service up to once per hour to determine when new data should be delivered via your connector.

Here is the recommended workflow:

![Screen Shot 2022-08-10 at 8.37.38 AM](https://solutions.narrative.io/hubfs/Screen%20Shot%202022-08-10%20at%208.37.38%20AM.png)

1. Authenticate to the Narrative API using our OAUTH workflow utilizing your app secret and your app ID, and receive a token scoped to the user utilizing the app.
2. Use the token to GET a list of deliveries from the [Deliveries API service](https://api.narrative.dev/#tag/Subscriptions/paths/~1data-shops~1subscriptions~1%7Bsubscription_id%7D~1deliveries/get).
3. Use the token to GET a list of delivery commands from the [Deliveries API service](https://api.narrative.dev/#tag/App-API/paths/~1v1~1app~1commands~1delivery/get). Each delivery command will contain a subscription ID or dataset ID indicating the object that has been updated, an incremental offset for the delivery (which you can use to track which deliveries have been provided already, a profile ID and a Quick Settings JSON blob. These settings are required for you to know where to deliver each file.
4. GET a list of delivery files for a command from the [Delivery Files API service.](https://api.narrative.dev/#tag/App-API/paths/~1v1~1app~1commands~1delivery~1%7Bdelivery_id%7D~1files/get)
5. For each delivery file, POST to the [Download API](https://api.narrative.dev/#tag/Subscriptions/paths/~1data-shops~1subscriptions~1%7Bsubscription_id%7D~1deliveries/get) to retrieve an AWS s3 pre-signed URL to download a file delivered as part of the subscription. Download the file once and store for delivery.

### Deliver Data

Once you have downloaded data from the Narrative platform, your app is responsible for using your own API or other infrastructure to deliver the data to your user.
