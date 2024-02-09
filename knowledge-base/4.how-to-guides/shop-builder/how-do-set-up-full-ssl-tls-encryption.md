---
title: 'How do I set up full SSL/TLS encryption for my Data Shop?'
description: 'Point your registered domain to Cloudflare nameservers for full SSL/TLS encryption.'
lastUpdated: '2021-08-17T14:53:39.161Z'
tags: ['Selling Data', 'Data Shops']
---
Narrative will manage the full SSL/TLS encryption of your Data Shop through Cloudflare. To set up SSL/TLS encryption for your registered domain, please follow these instructions.  

1. **Log in** to the administrator account for your domain registrar (e.g. GoDaddy).
2. **Remove** the existing nameservers.
3. **Add** Cloudflare's nameservers:

    aria.ns.cloudflare.com

    santino.ns.cloudflare.com

4. **Save** your changes.

Registrars can take 24 hours to process nameserver updates.

Once this is done, your Data Shop will benefit from full SSL/TLS encryption, using a self signed certificate on the server.
