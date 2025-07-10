## Data Usage Reduction

## Table Scans

Think of a full table scan as a full search of all records in a given table; effectively a `select *` in SQL terms. As tables get larger and larger, this operation becomes more expensive. The about of `bytes` processed will continue to increase leading to increased cost. As you might expect, we should avoid scanning entire tables when creating queries or setting up dashboards connected to tables in a database.


## BigQuery Cost Overview


### Storage Costs

1. Active Storage: This is the cost for storing data that is frequently accessed. 
2. Long-Term Storage: Data that is not modified for 90 days is considered long-term storage and is charged at a lower rate than Active Storage tables.

### Compute Costs

The amount of money charged based on the amount of data processed by your queries. This is  where cost can get out of hand especially when frequent `table scans` are performed!


## Reducing Bigquery Cost


### Full Table Scan Cost

In Figure 1, you can see how much data a full table scan uses on my test table. A full scan uses 4.09 GB. Without any optimizations, if this was connected to a looker dashboard, each time a filter would be applied, 4.09 GB would be used to accomplish that task! As you might recognize, this can add up dramatically fast.

<figure align="center">
    <img src="../imgs/SOP/Full Table Scan.png" width="95%">
  <figcaption>Figure 1: Full Table Scan</figcaption>
</figure>

### Use columns you actually need

**Having more is not better. Having what you need is critical**.

<br>


<figure align="center">
    <img src="../imgs/SOP/Choose Your Columns.png" width="95%">
  <figcaption>Figure 2: Reduction Of Usage Based On Columns Selected </figcaption>
</figure>

<br>
<br>

As you might imagine, the less columns you select, the less data needed to be processed is required to perform the query. Just by selecting the columns I needed, I reduced the total usage of my query by over 90%. When building tools, tables, and dashboards, be mindful of the columns you create and actually use. `A lot of times, extra columns typically do not get used and get ignored. These columns will then only contribute to increasing the bill.`


### Partition Your Tables

Partitioning can help drastically reduce costs especially when the data is continuous with time. Your partition you select for your table must be either a date or integer type and be the primary filter in your looker dashboard. For more details about partitioning, please click [here](https://github.com/CarrierOps/1P-Wiki/blob/main/Data%20Handbook/partitioning_and_clustering.md).



### Limit the amount of tables being referenced in your dashboard

The more tables you bring in and do operations on in looker, the higher the cost will be when users start to apply filters to the dashboard. Ideally, you should just have one table that powers a dashboard that contains `everything that you need not everything you can think of`. This will reduce the amount of data computation looker will have to do. If that is not possible, be as concise as possible with how many tables you bring in. Ideally, looker should not be doing the bulk of the calculations.


### Let BigQuery handle the calculations and calculated fields

As much as physically possible, let BigQuery handle the calculations and not looker studio. Create the columns `you need` and import that into Looker with all of the above optimizations. Using the `data blend` feature in Looker seems nice at first, but when the logic gets complicated with many tables being added in, the amount of data used will be `astronomically higher` then just doing all of the calculations within Bigquery and importing that table into looker.




