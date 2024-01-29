---
title: 'Multi-Data Plane Queries Not Supported'
description: "NQL queries cannot be run across multiple data planes.  This is a known limitation of the NQL language."
lastUpdated: '2024-01-29'
tags: ['nql', 'data plane', 'query']
---

## Overview

NQL queries cannot be run across multiple [data planes](/knowledge-base/concepts/key-narrative-concepts/what-is-a-data-plane).  This is a known limitation of the NQL language.

## Why is this a limitation?

NQL queries currently can only be executed on a single data plane.  A data plane is a hosted environment where data lives.  Separate data planes give customers to better control their data and how it is accessed.  For example, a customer may have a data plane for their own data and a separate data plane for data they have purchased from a third party.  This separation of data is a key security feature of the Narrative platform.

## Troubleshooting Steps

- **Verify Data Location**:  If you are receiving this error, it is likely that you are attempting to run a query across multiple data planes.  Verify that all data referenced in your query is located in the same data plane.
- **Modify Query**: If you are unable to modify your data location, you will need to modify your query to only reference data in a single data plane.
