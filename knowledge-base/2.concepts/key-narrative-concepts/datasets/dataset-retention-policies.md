---
title: Dataset Retention Policies
description: Understanding Dataset Retention Policies at Narrative
lastUpdated: '2024-03-27T19:28:46.247Z'
tags:
  - Integrations & Technical Guides
  - Datasets
  - Deleting Data
  - Narrative Syncs & Processes
---

#### Overview

In the dynamic environment of Narrative, managing the lifecycle of datasets is a fundamental part of data stewardship. Dataset retention policies are crucial for ensuring data is stored only for as long as necessary, optimizing storage usage, and maintaining compliance with various data governance protocols.

#### What Are Dataset Retention Policies?

A dataset retention policy in Narrative is a set of rules that governs how long data within a dataset should be retained before automatic deletion. Organizations can establish retention policies that reflect their legal, operational, or business-driven data retention requirements.

#### Default Deletion & Retention Periods

When a dataset is deleted through the API or UI, Narrative institutes a default 30-day retention policy. This means that the data will be marked for deletion and purged after 30 days, unless a different retention policy is specified. This delay is designed as a protective measure to mitigate against accidental deletions and to provide an opportunity to restore the dataset if necessary.

#### Immediate Data Deletion and Custom Retention Policies

For immediate data deletion or custom retention beyond the default 30-day period, users can pre-emptively adjust the policy prior to deleting the dataset. It's important to note that setting a custom retention policy can help manage costs as well as ensure adherence to specific data governance standards.

#### API Specification for Dataset Retention Policies

The Narrative API provides the ability to define and adjust dataset retention policies programmatically. Here is a brief overview of the parameters and request body schema to set retention policies:

##### Path Parameters:

\- `dataset_id` (required, integer): The unique identifier for a dataset.

##### Request Body Schema:

The request body must match one of the following types with the associated properties:

- `ExpireEverything`
- `RetainEverything`
- `ExpireWhen`
- `RetainWhen`

For the purpose of setting a custom retention policy, the `expire_when` type is often used with the following properties:

- `type` (required, string): Should be set to `"expire_when"`.
- `expression` (required, object): Details the conditions under which data should expire.

###### `expression` Object:

- `type` (required, string): Must be `"snapshot_age"` for specifying retention based on age of the data snapshot.
- `operator` (required, string): One of the comparison operators (\`">"\`, `"<"`, `">="`, or `"<="`).
- `period` (required, string): Defines the period in ISO 8601 format, dictating after what period data should expire.

Using these API specifications, users can tailor dataset retention policies to meet specific needs, whether for cost control or compliance with data protection regulations.

###### Example Request Object

HTTP: `https://api.narrative.io/datasets/dataset-id/retention-policy`

```text
{
    "dataset_id": dataset-id,
    "type": "expire_when",
    "expression": {
        "type": "snapshot_age",
        "operator": ">",
        "period": "P90D"
    }
}
```

#### Conclusion

The flexibility offered by Narrative to manage dataset retention policies ensures that users can handle their datasets effectively. With clear understanding and proper implementation of retention policies, organizations can maintain optimal data storage practices, protecting sensitive information and aligning with budgetary constraints.

Always refer to the most current \[Narrative I/O API documentation]\(<https://api.narrative.io/>) for the latest guidelines and API usage details.
