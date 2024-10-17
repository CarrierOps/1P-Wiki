# TMO GP Mobile Sales Data Documentation

## Summary
The TMO GP sales data pipeline takes data from a `csv` file sent to us by email.


## Cadence
Whenever they send data us via email(usually weekly).

## Flowchart
**WIP**




## Pipeline Details

1. Columns are renamed and formatted to `snake case`
2. Product names are then mapped to an imported table using sku_code.
3. A `uid` is created from the concatenation of the columns `transaction_date`, `sku_code`, `product_descriptions`, `imei`,`store_name`.
4. Data types are then enforced to be consistent with the nature.
5. The data is then exported to BigQuery using a `MERGE STATEMENT` and GCS a clean `parquet` file is sent to the `clean` subfolder with the `tmo_gp_mobile` folder. 