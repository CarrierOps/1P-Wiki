TMO Mobile One Inventory Pipeline

## Summary
The TMO Mobile One data pipeline takes data from a Google sheet and brings that data into BigQuery.

## Cadence
The pipeline is schedule to run on **Tuesdays's at 9am EST**.


## Flowchart
**WIP**


## Details In Pipeline
1. Columns are renamed and formatted to `snake case`
2. Product names are then mapped to an imported table using sku_code.
3. The data is then `LEFT JOINED` with our `MSL` i.e. `Inventory LEFT JOIN MSL` using `retail_id`.
4. A `uid` is created from the concatenation of `date`,`time`, `retail_id`, `starting_soh`, `movement_qty`, `ending_soh`, `user_id`,`serial_number`, and `sku_description`.
5. Data types are then enforced to ensure the consistency of the data.
6. The data is then exported to BigQuery using a `MERGE STATEMENT` and GCS a clean `parquet` file is sent to the `clean` subfolder with the `tmo_mobile_one` folder.
