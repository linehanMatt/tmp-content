---
title: 'How Access Rules Work'
description: 'Access Rules are the backbone of data access control in Narrative''s Data Collaboration Platform. '
lastUpdated: '2023-06-09T21:12:44.659Z'
tags: ['Welcome to Narrative', 'How Narrative Works']
---
The data in a dataset can never be accessed by any entity unless access is granted by configuring an Access Rule. Access Rules in Narrative’s platform can be thought of as an evolution of the traditional database “view”: they define exactly what subset of a dataset or multiple datasets can be queried, as well as who gets access to that data, and how they can use it.

#### Query

The Query component of an Access Rule selects a specific subset of your data. Collaborators can access this subset as if it were a completely new dataset, without the need to actually generate and populate a new dataset.

#### Policy

The Policy aspect of Access Rules lays out the guidelines for how your data is accessed and used. It details which collaborators have the authority to access the data. It also outlines the kind of operations, such as analysis rules, that collaborators can carry out on the data. Finally, it determines where they can dispatch the results of their data operations, referred to as output rules. This ensures structured and controlled data access and operations within Narrative's platform.

#### Governance

The Governance component of Access Rules defines the terms and conditions for data access. It sets a price per row for access, if there is one, and establishes the license conditions, which could vary from public domain to specific licensing agreements. This data is incorporated into the query results on a row-by-row basis to ensure that all downstream data access adheres to these specified terms.
