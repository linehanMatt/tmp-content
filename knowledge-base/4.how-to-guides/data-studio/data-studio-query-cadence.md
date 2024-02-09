---
title: 'Data Studio: Query Cadence'
description: 'Customize the timeline of your data deliveries. '
lastUpdated: '2021-12-08T21:53:23.193Z'
tags: ['Buying Data', 'Buyer Studio']
---
# Refresh Schedules in Data Studio with NQL

Materialized views in the Narrative Data Collaboration platform provide a powerful way to store the results of complex queries for quick access. But what makes these views particularly valuable is their ability to stay up-to-date with a feature known as the "refresh schedule." This capability allows materialized views to periodically update their data, ensuring analysts and business users are always working with the latest information.

## Understanding Refresh Schedules in Materialized Views

When creating a materialized view using NQL, you can define how frequently the view should be refreshed by setting the `REFRESH_SCHEDULE` option within the query's metadata. This option dictates when and how often the data should be updated, be it hourly, daily, weekly, or at other custom intervals.

The `REFRESH_SCHEDULE` accepts cron expressions for fine-grained control, as well as preset interval strings like `@hourly`, `@daily`, `@weekly`, `@monthly`, and `@once`. These settings ensure that your materialized views remain an accurate reflection of the underlying datasets.

## Example of a Materialized View with Refresh Schedule

To provide a practical example, let's create a materialized view of sales data that refreshes at the start of each week:

```nql
CREATE MATERIALIZED VIEW "weekly_sales_summary"
  DISPLAY_NAME = 'Weekly Sales Summary'
  DESCRIPTION = 'A summarized view of weekly sales data.'
  STATUS = 'active'
  TAGS = ('weekly', 'sales', 'summary')
  WRITE_MODE = 'overwrite'
  EXTENDED_STATS = 'all'
  REFRESH_SCHEDULE = '@weekly'
AS
SELECT
  DATE_TRUNC('week', "sales_data"."transaction_date") AS "week_start_date",
  SUM("sales_data"."amount") AS "weekly_sales_total"
FROM
  "company_data"."sales_data"
WHERE
  "sales_data"."transaction_date" > CURRENT_DATE - INTERVAL '6 months'
GROUP BY "week_start_date"
```

In this NQL statement, we are creating a materialized view called "weekly_sales_summary" that will aggregate sales data on a weekly basis. The `REFRESH_SCHEDULE` is set to `@weekly`, which will automatically update the view at the start of each week.

## Metadata Options for Materialized Views

Aside from the refresh schedule, several metadata options help further define the behavior and characteristics of the materialized view:

- `DISPLAY_NAME`: A user-friendly name for the view that makes it easily identifiable.
- `DESCRIPTION`: A brief explanation of the view's contents and its intended use.
- `STATUS`: The operational state of the view, such as 'active' for an in-use view.
- `TAGS`: A list of descriptive keywords or phrases to categorize the view, automatically including '_nio_materialized_view'.
- `WRITE_MODE`: `overwrite` to update the entire view with new data, or `append` to add new data leaving the old data intact.
- `EXTENDED_STATS`: Including 'all' will ensure comprehensive statistics are collected, while 'none' will skip additional stats.
- `PARTITIONED_BY`: Allows segmenting the view data into partitions for more efficient querying.

By configuring these metadata options thoughtfully, you can create materialized views that not only serve as snapshots of your data but also adapt to the evolving needs of your analysis.

## Conclusion

Materialized views with refresh schedules are a pivotal feature within Data Studio's NQL toolbox, drastically improving the relevance and timely access to data. Whether you’re a data analyst monitoring performance metrics or a marketing strategist analyzing campaign trends, the ability to set a refresh schedule ensures that your views always reflect the most current data, thereby supporting more accurate insights and decisions.

For further exploration and to create your own materialized views, dive into the [Data Studio UI](https://app.narrative.io/platform/data-studio) and leverage the power of NQL to shape your data narrative.
