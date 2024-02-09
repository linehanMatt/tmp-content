---
title: 'Building a Narrative Native App'
description: 'Building a Narrative Native App is an easy way for third party developers to extend the capabilities of the Narrative platform'
lastUpdated: '2022-12-10T18:12:00.646Z'
tags: ['Integrations & Technical Guides', 'Overview']
---
### What is a Narrative Native App?

Narrative Native Apps are applications bundled with a UI that can perform various actions on behalf of a user utilizing the Narrative API.

### Narrative Native App Components

The following components make up a Narrative Native App:

1. **App Manifest:** A JSON blob that describes the required permissions, address of the app-hosted UI, configuration information and navigation pages required to render the app in the Narrative platform.
2. **Auth:** Through an OAuth workflow, the Narrative Native App will be granted permissions to act on behalf of users that install the app.
3. **Narrative APIs:** Based on the permissions they have been granted, Native Apps make calls

### Narrative Native App Types

### Functional Apps

Extend Narrative platform functionality with a functional app. These are the most basic form of app, and are able to perform actions on the platform consistent with the API service permissions defined in their manifest.

### Egress Connector Apps

Egress Connector Apps provide delivery of data from the Narrative platform to third party destinations. Egress connector apps are notified via an event bus when there is data that needs to be delivered downstream.

Connector Apps additionally extend the functionality of other installed apps: Connector Apps appear in the “Destinations” section of the Dataset Manager app, the Data Marketplace, and elsewhere in the platform.

### Ingress Connector Apps

Ingress Connector Apps provide new locations from which Narrative can ingest data.

### Channel Apps

Channel Apps are apps that can take an existing Narrative Data Stream and deliver it to a specific channel (such as the AWS Data Exchange or The TradeDesk third party marketplace API).

Because Data Stream data is only processed when a Data Stream subscription is created, Channel Apps must materialize Data Streams (create a new Dataset based on the Data Stream data) and deliver that dataset to their destination.

### External Function Apps

External Function Apps provide access to a third party REST API service. Users will configure their API credentials and other necessary account information in the External Function App. External Functions can then be mapped to individual fields within Datasets, which will be augmented with data returned from the app.

### Narrative App Manifest

The App Manifest provides the Narrative platform with the following information, which is required in order to render your app. You can see the full, up to date JSON schema required for an app [here](https://json-schemas.narrative.dev/v1/app_manifest_schema.json).

App Manifests provide, at a minimum:

* Base URLs for development and production sites where the app’s UI is hosted
* Path to each of the pages in the app, for the Narrative Nav to render
* Narrative API permissions that your app requests when users install the app. These are the Narrative API permissions your app can perform on the user’s behalf in order to function
* Developer information so that users know who they are interacting with when they install your app.

### Narrative App User Interface

#### **App UI**

The user interface you host will appear within the Narrative UI. It will be available within the app when the user launches your app. It will have two components:

* **Narrative Navigation**: All Narrative Native Apps share the Narrative navigation bar, which contains links to each page in your app as defined in your manifest (individual site page with a unique URL).
* **Developer-hosted iFrame**: This is where the content of your hosted app UI will appear when a user navigates to one of the pages you define.

![narrative-native-app](https://solutions.narrative.io/hubfs/narrative-native-app.png)

### Narrative Native App OAuth Workflow

In order to authenticate on behalf of a user, a Narrative Native App will use the Narrative OAuth workflow below. See the [Narrative Auth service documentation](https://api.narrative.dev/#tag/Auth/paths/~1oauth~1token/post) for more details.

In order to utilize the Narrative OAuth workflow, you will need:

* Your app-specific client\_id that was shared with you when your app was created
* Your app-specific client\_secret that was shared with you when your app was created

### Offline OAuth Workflow

Utilize this workflow when your app needs to access the Narrative API but the action has not been triggered by a call to your UI.

1. Send a request to the [Narrative API Auth Service](https://api.narrative.dev/#tag/Auth/paths/~1oauth~1token/post) containing the client\_id and client\_secret
2. Receive an access\_token and a TTL for the access token, along with a refresh\_token and a TTL for the refresh token.
3. Use the access\_token for all calls to the Narrative API until a refresh is required. If the access token expires, utilize the refresh token to get a new one.

### iFrame OAuth Workflow

Utilize this workflow when the Narrative UI iFrame renders your app UI.

The Narrative App Framework will call the UI with an API access\_token that is authenticated to the App User’s company. The permissions and scope of this token are restricted to those that your App permissioned at install time.

### How can I get started?

To get started building, reach out to your account manager.
