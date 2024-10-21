# 2024 Advocacy Survey Data Pipeline

## Summary
This pipeline 4 different tabs from a google sheets and ingests that data into BQ. This data comes from survey123 and is brought into sheets using powerautomate.

## Cadence
Every hour near minute 0.

## Flowchart
**WIP**

## Details In Flowchart

1. Columns are renamed and formatted to `snake case` and cleaned such that they can be properly ingested into BigQuery.
2. The 4 different tabs from survey are then vertically concatenated(combined using a union all).
3. The pipeline then sends a job to BigQuery to replace the current table with the new table created with the new table.