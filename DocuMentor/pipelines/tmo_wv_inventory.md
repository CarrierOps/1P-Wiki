# TMO Wireless Vision Inventory Data Documentation

## Summary
The TMO Wireless Vision sales data pipeline takes data from a `csv` file sent to us by email.


## Cadence
Whenever they send data us via email(usually weekly).

## Flowchart
**WIP**

## Details In Pipeline
1. Columns are renamed and formatted to `snake case`

2. The data is then `LEFT JOINED` with our `MSL` i.e. `Inventory LEFT JOIN MSL` using `retail_id`.
3. A `uid` column is created from `retail_id`, `total_units`,`sku_description`, and `date` columns.
4. Data types are then enforced to ensure the consistency of the data.
5. The data is then exported to BigQuery using a `MERGE STATEMENT` and GCS a clean `parquet` file is sent to the `clean` subfolder with the `tmo_wireless_vision folder.


