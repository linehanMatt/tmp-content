---
title: 'How do I point my domain to my Data Shop in Cloudflare?'
description: 'Learn how to connect your custom domain to your Data Shop using Cloudflare.'
lastUpdated: '2021-08-05T15:41:43.543Z'
tags: ['Selling Data', 'Data Shops']
---
### Overview

Your Data Shop domain is the part of a URL after "https://www.". For example, the Narrative Data Streams Marketplace domain is **app.narrative.io**.

Follow this guide to use Cloudflare to point your domain to your Data Shop in few simple steps:

1.  Create CNAME records for your domain and your www URL
2.  Set up a forwarding URL for your www domain
3.  Turn on full SSL/TLS encryption

### Create CNAME Records in DNS Settings

A  Canonical Name Record or CNAME record is used to alias one domain name (or subdomain name) to another.

You will create two CNAME records in Cloudflare: one for your **naked domain**, and one for your **www domain**.

Go to **DNS management** for your domain in Cloudflare to create CNAME records. ![](https://solutions.narrative.io/hubfs/undefined-Jun-25-2021-01-19-55-99-AM.png)

#### **1\. CNAME Record for Naked Domain**

1.  Click **Add Record**.
2.  For the record Type, select **CNAME**.
3.  Enter your domain (e.g. **yourdatashop.com**) into the Name field.
4.  Copy and paste this URL into the Target field:
    
    data-shops.narrative.io
    
    1.  **Note:** You can also use data-shops-dev.narrative.io 
5.  **Save**.

![](https://solutions.narrative.io/hubfs/undefined-Jun-25-2021-01-10-02-74-AM.png)  

#### **2\. CNAME Record for www Domain**

1.  Click **Add Record**.
2.  For the record Type, select **CNAME**.
3.  In the Name field, enter **www**
4.  Copy and paste this URL into the Target field: 
    
    data-shops.narrative.io
    
5.  **Save**.

![](https://solutions.narrative.io/hubfs/undefined-Jun-25-2021-01-12-45-92-AM.png)  

### Set Up a Forwarding URL in Rules

Go to **Rules** for your domain in Cloudflare.

![](https://solutions.narrative.io/hubfs/undefined-Jun-25-2021-01-19-16-82-AM.png)

1.  Click **Create Page Rule**. ![](https://solutions.narrative.io/hubfs/undefined-Jun-25-2021-01-20-59-18-AM.png)
2.  In the "If the URL matches" URL field, enter:
    
    www.\[YOURDOMAIN.COM\]/\* 
    
3.  Select **Forwarding URL**.
4.  Select **302 - Temporary Redirect**.
5.  In the bottom URL field, enter:
    
    https://\[YOURDOMAIN.COM\]/$1
    
6.  Make sure your new rule resembles this screenshot, but using your custom domain instead of **yourdatashop.com**, and **Save**.![](https://solutions.narrative.io/hubfs/undefined-Jun-25-2021-01-24-31-00-AM.png)

### Turn on Full SSL/TLS Encryption

Navigate to the **SSL/TLS** section of your domain on Cloudflare.

![](https://solutions.narrative.io/hubfs/undefined-Jun-25-2021-11-33-12-29-AM.png)

Make sure your SSL/TLS encryption mode is **Full**. ![](https://solutions.narrative.io/hubfs/undefined-Jun-25-2021-11-33-57-80-AM.png)

Your changes may take a couple of minutes to propagate. Then, when you visit your domain, you should see your Data Shop. 

Something not working as expected? Please use the chatbot or reach out to support@narrative.io for help.

If you want to set up your data shop on a testing environment instead of a production environment, please use data-shops-dev.narrative.io instead of data-shops.narrative.io.
