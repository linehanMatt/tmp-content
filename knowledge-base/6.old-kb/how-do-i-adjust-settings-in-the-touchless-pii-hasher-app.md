---
title: 'How do I adjust settings in the Touchless PII Hasher app?'
description: 'Understand the different options to hash emails using Narrative''s Touchless PII Hasher app.'
lastUpdated: '2023-04-28T15:52:11.991Z'
tags: ['Touchless PII Hasher', 'Touchless PII Hasher']
---
### Overview

Different email hashing options are available in the [Touchless PII Hasher app](https://app.narrative.io/#/app/touchless-pii-hasher). You can change your app settings via the **Hash Settings** dropdown menu. The available settings are explained below.

By default, the app hashes raw email addresses according to 3 hashing algorithms (SHA-256, SHA-1, and MD5) and removes invalid email addresses before hashing.

**![](https://solutions.narrative.io/hubfs/undefined-1.png)**

### Touchless PII Hasher Settings

#### SHA-256 Hash

Select this option to generate a SHA-256 hash for each valid email address in your file. The resulting SHA-256 hashes will be saved as a new column.

This setting is active by default.

#### SHA-1 Hash

Select this option to generate a SHA-1 hash for each valid email address in your file.

This setting is active by default.

#### MD5 Hash

Select this option to generate an MD5 hash for each valid email address in your file.

This setting is active by default.

#### Include Original

Choose this option to generate a file with your original raw email addresses in one column and new hashed email addresses appended as new columns.

This setting is NOT active by default.

#### Remove Invalid Emails

Select this option for the Touchless PII Hasher to generate hashes only for valid, properly formatted email addresses.

This setting is active by default.

### Additional Resources

[How do I use the Touchless PII Hasher app?](https://kb.narrative.io/how-do-i-use-the-touchless-pii-hasher-app)

[Blog Post: Convert email addresses into privacy-safe identifiers with Touchless PII Hasher](https://blog.narrative.io/touchless-pii-hasher)

[What does the term "hash" mean?](https://kb.narrative.io/what-is-hashing)

[How do I hash a list of emails?](https://kb.narrative.io/how-do-i-hash-an-email-mac-os)
