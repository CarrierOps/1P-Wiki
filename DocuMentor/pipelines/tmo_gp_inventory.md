# TMO GP Mobile Inventory Documentation

## Summary
The TMO GP Invenbtory data pipeline takes data from a `csv` file sent to us by email.


## Cadence
Whenever they send data us via email(usually weekly).

## Flowchart
**WIP**


## Details In Pipeline
1. Columns are renamed and formatted to `snake case`

2. The data is then `LEFT JOINED` with our `MSL` i.e. `Inventory LEFT JOIN MSL` using `retail_id`.
3. A `uid` column is created from the concatenation of `date`, `sku_code`,`on_hand_sellable`,`on_hand_non_sellable`,`quantity`,`retail_id` columns.
4. Data types are then enforced to ensure the consistency of the data.
5. The data is then exported to BigQuery using a `MERGE STATEMENT` and GCS a clean `parquet` file is sent to the `clean` subfolder with the `tmo_gp_mobile` folder.
6. A `gold layer` table is then created using SQL sent as a bigquery job which creates enriches the inventory data by creating a daily inventory dataset. This table is called `tmo_gp_mobile_inventory_gold`.  
