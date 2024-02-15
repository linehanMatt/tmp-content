---
title: 'How to Create an API Token'
description: 'A simple guide for developers on generating an API token within the Narrative platform, ensuring secure and authorized API access.'
lastUpdated: '2023-04-24T23:05:19.054Z'
tags: ['API', 'Authentication', 'Security', 'Developer Guide']
---

## How to Create an API Token

Creating an API token is a crucial step for developers to securely authenticate requests to the Narrative API. This guide walks you through the process in a few simple steps.

### Step 1: Navigate to API Key Management

Navigate to the [API Keys](https://app.narrative.io/platform/settings/api-keys) section of the UI (under "Settings" -> "API Keys"). 

### Step 2: Create a New API Key

Click on **Create New API Key+**. You will be prompted to configure your new API key.

### Step 3: Configure Your API Key

- **Name**: Give your API key a meaningful name that represents the app or purpose it will fulfill. For example, "Snowflake Native App Integration".
- **Expiration Date**: Set an expiration date for the API key to enhance security. Note that max expiry is 1 year from today. 
- **Permissions**: Select only the permissions necessary for the API key to perform its intended functions. Refer to the API key permissions section in the UI documentation for guidance on what permissions to grant.

### Step 4: Store Your API Token Safely

Once created, the API token will be displayed **one time only**. Use the copy button to store it securely, as you will not be able to retrieve it again.

### Best Practices

- **Minimum Permissions**: Always grant the minimum permissions needed for the API key's intended use.
- **Regular Rotation**: Regularly update the expiration date and rotate API keys as a security best practice.

### Revoking an API Key

If needed, you can revoke an API key by navigating to the API Keys section, clicking the "..." button next to the key, and selecting "Delete". This immediately invalidates the API key.

For security incidents, revoke all API keys, create new ones, and report the incident to Narrative security.


## More information
For more information, please see the knowledge base article on [API Keys](/knowledge-base/ui-documentation/settings/api-keys). 
