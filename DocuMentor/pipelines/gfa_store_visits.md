# GFA Store Visits Pipeline

## Summary
This pipeline takes daily data from a Google P=plx trix and brings that data into BigQuery. This data pertains specifically to visits recorded with no survey results.

## Cadence
Every day at 9 am EST.

## Flowchart 
**WIP**


## Pipeline Details
1. A Google Plx Trix is setup to pull the `GFA` data into a google sheet daily.
2. A Google App Script is used to extract the daily data from the Plx Trix which will be stored in GCS as well as be used to fire off the pipeline. 
3. Reformat columns ensures columns are in snake case i.e. snake_case
4. A uid is created form columns `ice_store_id`, `visit_type`, `start_date_time`, `end_date_time`, and `store_visit_id`.
5. The `uid` is needed for the `Merge Data Into BigQuery block` as it in ensures that every single entry is unique and no data will be added into the table in BigQuery where the uid already exists.
6. Columns data types are then enforced to make with the context of the data.