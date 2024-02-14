---
title: API Keys
description: Guides to help you with managing API keys
---

API keys are used to authenticate requests to the [Narrative API](https://api.narrative.dev).  They may be used by developers who are calling those APIs directly, or by other systems that are making requests on behalf of users.  This guide will help you manage your API keys.

## Your Existing API Keys

You can view your existing API keys by navigating to the [API Keys](https://app.narrative.io/platform/settings/api-keys) section of the "Settings" page.  You will see a list of your existing API keys, along with their expiration dates and the permissions given to that key.

### API Key Permissions

API keys can be given different permissions, depending on what you need them to do.  Most Narrative API endpoints have their own permissions boundaries in addition to the access (Read / Write) that is granted to the API key.  

As an example all of the API endpoints under `/data-planes` require the `data-planes` permission to be granted to the API key.  A key may be given Read Access or Write Access or both.

#### Best Practices for API Key Permissions

When creating an API key, you should give it the minimum permissions necessary to perform its intended function.  This is a security best practice, and it will help protect your data and your account from unauthorized access.

### API Key Expiration

API keys can be given an expiration date, after which they will no longer be valid.  This is another security best practice, and it will help protect your data and your account from unauthorized access.

We **highly** recommend setting an expiration date for all API keys and rotating them regularly*

## Creating a New API Key

Create a new API key by clicking the "New API Key" button on the [API Keys](https://app.narrative.io/platform/settings/api-keys) page.  You will be prompted to give the key a name and to select the permissions and expieration date you want to grant to the key

## Revoking an API Key

You can revoke an API key by clicking the "..." button next to the key on the [API Keys](https://app.narrative.io/platform/settings/api-keys) page and selecting "Delete".  This will immediately revoke the key and it will no longer be valid for making requests to the Narrative API.

If you have experienced a security incident, you should revoke all of your API keys and create new ones.  This will help protect your data and your account from unauthorized access.  You should also report the incident to [Narrative security](security@narrative.io) so that we can help you investigate and take appropriate action.
