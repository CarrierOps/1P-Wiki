# TMO Connectivity Inventory Data Documentation

## Summary
The TMO Connectivity Inventory data pipeline takes data from a `xlsx` file sent to us by email.


## Cadence
Whenever they send data us via email(usually weekly).


## Flowchart
**WIP**

## Details in Flowchart

1. Columns are renamed and formatted to `snake case`

2. The data is then `LEFT JOINED` with our `MSL` i.e. `Inventory LEFT JOIN MSL` using `retail_id`.
3. A `uid` column is created from the concatenation of the  `shipped_to`,`shipped_from`, `delivery_confirmation_date`,`delivery_order`, and `serial_number` columns.
4. Data types are then enforced to ensure the consistency of the data.
5. The data is then exported to BigQuery using a `MERGE STATEMENT` and GCS a clean `parquet` file is sent to the `clean` subfolder with the `tmo_connectivity` folder.


