---
title: 'Understanding Attribute Lineage in Materialized Views'
description: 'An explanation of how attribute mappings persist across materialized views.'
lastUpdated: '2024-02-29'
tags: ['NQL', 'Data Collaboration', 'Rosetta Stone', 'Materialized Views']
---

Attribute lineage refers to the tracking and management of Rosetta Stone attribute mappings during Materialized View creation, especially when it is transformed or integrated from various sources. This concept is crucial in ensuring data consistency, quality, and accessibility in complex data environments. This article delves into the attribute lineage based on a specific product specification, illustrating how attribute mappings can be persisted in the creation of Materialized Views from datasets or access rules.

## Introduction to Attribute Lineage

In data management, maintaining the lineage of attribute mappings is essential when creating Materialized Views from existing datasets. Often, datasets are already mapped to specific Rosetta Stone attributes Manually re-mapping these attributes for Materialized Views can be redundant and inefficient, especially when the data transformation process does not alter the original data structure or semantics. The attribute lineage feature aims to automate and preserve attribute mappings under certain conditions, streamlining the data management process.

## Scenarios for Persisting Attribute Mappings

Persisting attribute mappings in Materialized Views is feasible under three primary scenarios:

1. **Direct Selection of Unaltered Attributes**: When a user selects a Rosetta Stone attribute directly from a dataset or access rule without modifying its output (e.g., through data functions), the attribute mapping should be preserved. Aliasing the attribute (e.g., `SELECT x AS y`) does not count as altering the data.
   
2. **Selection from an Existing Materialized View**: Selecting attributes directly from an already created Materialized View should also preserve the attribute mappings, as these views are considered to have maintained the integrity of the original mappings.

3. **Comprehensive Selection of Unmanipulated Fields**: When a user selects all fields or columns constituting an attribute mapping without manipulating any of these elements, the resulting dataset should retain the original mappings.

## Implementation of Attribute Lineage

Attribute lineage can be implemented through:

1. **Implicit Usage-Based Remapping**: This involves automatically remapping attributes based on their usage within the dataset properties. For instance, if a dataset includes a `Raw Email` attribute mapped through an `value` property, creating a Materialized View that selects the `value` property should implicitly remap the `Raw Email` attribute to the new view.

2. **Identity Mappings for Dataset Attributes**: When attributes are queried from specific datasets, especially when using the `_rosetta_stone` namespace, the resulting Materialized View should inherit mappings to all properties of the selected attribute, irrespective of the mappings present in the source dataset.

3. **Identity Mappings for `rosetta_stone` Attributes**: Similar to dataset-specific attributes, querying attributes from a `rosetta_stone` table and creating a Materialized View should also result in the view inheriting mappings to all properties of the queried attribute.

### Considerations for Derived Mappings

- **Scope, Source, Tags, and Status**: These properties are inferred or copied from the original mapping, with specific rules adjusting based on the context (e.g., `scope` might be set to `GLOBAL` for `rosetta_stone` attributes, and `source` is usually set to `SYSTEM`).

- **Handling of Multiple Datasets and Colliding Mappings**: When multiple datasets contribute to a Materialized View and have overlapping attribute mappings, a prioritization logic determines which mapping is preserved, typically favoring the first dataset encountered in the query.

## Conclusion

Attribute lineage in the context of Materialized Views simplifies data management by automating the preservation of attribute mappings under specific conditions. This feature enhances data consistency and efficiency, especially in environments with extensive data transformation and integration processes. By understanding and leveraging attribute lineage, organizations can ensure that their data remains accurate, consistent, and easily manageable across different stages of data processing.