---
title: 'How do I get Started with Narrative''s Facebook Connector?'
description: 'Narrative''s Facebook Connector allows users to push data to their Facebook custom ad audience seat. '
lastUpdated: '2023-03-21T16:17:45.960Z'
tags: ['Data Egress Through Connector Apps', 'Facebook Connector']
---
### How to Set Up Narrative's Facebook Connector 

The Facebook Connector is a new app available on app.narrative.io. It serves as an endpoint for users to push data to Facebook's Custom Ad Audience endpoint and target individuals from their Facebook account. The app's setup process is similar to the S3 connector where users can install the app, set up a profile as a specific destination, and select the destination during checkout. In this article, we will walk you through the steps of setting up the Facebook Connector app in Narrative.

**Step 1: Register an Account with Narrative**  
If you have not already done so, register an account with Narrative. Go to the Narrative website (app.narrative.io) and click on the "Register" button on the top right corner of the homepage. Follow the prompts to create your account.

**Step 2: Install the Facebook Connector App**

Once you have created your account, install the Facebook Connector App. You can find the app in the "Apps" section of your client's account (app.narrative.io/apps).

![](https://lh6.googleusercontent.com/k7yacWqTGcvv-yssLy7ZV9nntjwj0nkLYM0TVbfQHp1w6NVF7KI_mKW_ctTPZALdcTPhRXRxrVRabcriIEaxmn0ITsJkw7ReRI8AXuIifYUeKiim_vU4iT1o3DG5_cqpiKNZnxJco9-eDQUZSCIaIMA)

**Step 3: Create a New Profile**

After you have installed the Facebook Connector app, create a New Profile by selecting the "New Profile" button in the top right corner. You will be prompted to OAuth your Facebook account by selecting the "Login with Facebook" button. It is important to verify that the correct user is associated with the account before clicking continue.

![](https://lh5.googleusercontent.com/qLaKl88Qv8xCcYEELeESZexpGeQ4LtgBieGyQaVnh0sbgGoE9EPZe5UF_CyIS5qZEDCCxyCdhL1sIA2i7UXeYkqc1_CQQy4VVtXrI5Po5vbWdqx4cVileeiMVXDOiwHi72AkVS8RCthCxM2rKam2EJg)

![](https://lh3.googleusercontent.com/a4EI6c7CkbYoxQGnBQWodiZn7up-dfkvhycHOFM6th3LZ1zQXzj1BGTnxw7fVOMgpeuVNxOCPlq2tCOX_W14BaB6RhEtsHE4vlhNdfx6ANIFZX9j5Dh3MxEv67hD-ytq3hnQuiBeYPJVoES8eET2ALI)

**Step 4: Adding the Correct Facebook Permissions**

Verify that the correct user is associated with your business account. Narrative needs ads\_management, business\_management, and public\_profile permissions for every account to properly write audiences. Narrative needs all of these permissions to deliver the relevant data.

**Step 5: Select the Facebook Ad Account**

Select the Facebook Ad Account you want to receive audiences in. If you have not set up custom audiences in [Facebook Business Media,](https://www.google.com/url?q=https://business.facebook.com/settings/partners/381182488719548?business_id%3D465873190594197&sa=D&source=docs&ust=1679417507674622&usg=AOvVaw3aOGq1H53UrILN1TsZ8OMW) you will not be able to toggle any of your accounts. 

**Step 6: Add a Profile Name and Description**

Add a profile name and description to help you identify the audience you are creating.

**Step 7: Activate the Profile**

Once you have added the necessary information, activate your profile. You will immediately be able to send audiences to that account.

**Step 8: Purchase Data**

Now that the Facebook Connector is set up and ready to use, the next step is to purchase the desired data. The Facebook Connector should show up as a "Destination" when creating a new Buyer Studio or Data Stream subscription.

![](https://solutions.narrative.io/hubfs/Screenshot%202023-03-21%20at%2012-15-12%20PM-png.png)

**Conclusion** 

By following the steps outlined in this article, you can seamlessly import custom audiences from Facebook into Narrative and acquire the data required for your marketing campaigns. However, it is important to note that the Facebook Connector is exclusively available for Buyer Studio and multi-provider Data Streams. Moreover, the connector can only create new audiences, and it cannot append to an existing audience, even if users title multiple audiences with the same name. Keep in mind that Buyer Studio orders can only include hashed emails, mobile advertising identifiers, birth information, gender, country code, and/or name, and deliveries must be under 100,000,000 rows.
