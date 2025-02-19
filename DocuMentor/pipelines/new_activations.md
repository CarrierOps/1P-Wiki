# New Activations Pipeline

## Summary
This pipeline is a remake of the previous activations pipeline. The previous version relied on a `seen_weeks` approach which filtered incoming data based on week values that were already ingested. This method albeit functional, would cause a lot of issues and hassle if data needed to be re-ingested. The remade pipeline does not use this method but rather ingests based on primary keys instead or the `uid` column.

## Cadence
The pipeline is scheduled to run **every Tuesday and Wednesday at ~12pm EST.**

*Note: The second pull time is subject to change*

## Pipeline Summary

1. A Google Plx Trix is setup to pull the activations data into a google sheet every week on Tuesday.
2. A Google App Script is used to extract the data from the Plx Trix which will be stored in GCS as well as be used to fire off the pipeline. Any new file added into the `raw` subfolders of the `activations_new` bucket is what is used to trigger a pipeline run.
3. We then concatenate all columns from the data pull to make our `uid` column or `primary key`. However, this is not truly unique as many duplicate `uid` values appear. To solve this issue, we group the data by all columns and aggregate by `acivation_count`. This ensures that the `uid` column is the primary key and is unique by row.
4. We then import state names and their long form from the `silver_layer.state_name_abbreviation` table in BigQuery. The aggregated data from the previous step is joined with this table using a `LEFT JOIN` on each datasets corresponding `state` columns. The result is a dataset that preserves the aggregated data from the previous step while adding columns from the `state_name_abbreviation` where states match.
5. A new column called `google_city` is created in the new dataset. This column is created by concatenating the columns `city` and `state`.
6. Proper data types are then enforced to ensure data consistency before exporting to Google Cloud Storage and BigQuery.
7. The cleaned data is then exported to `GCS`as a `parquet` file and then exported to BigQuery using a merge statement based on the `uid` column.
8. An update statement is performed right after to account for any late arriving data that could potentially increase the the aggregated `activation_count` per each `uid`. We accomplish this my importing the `uid` already existing within BQ and do a comparison check. If the `uid` values match and the associated `activation_count` is greater, then we set the `activation_count` within BQ to that new higher value. If the `activation_count` is equal to or lower than the current value in BQ, we do nothing and leave the current value as is.
