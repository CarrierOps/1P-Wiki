# TMO Connectivity Sales Documentation


## Summary
The TMO Connectivity sales data pipeline takes data from a `xlsx` file sent to us by email.


## Cadence
Whenever they send data us via email(usually weekly).


## Flowchart
**WIP**

## Details In Flowchart
**Note this may be subject to change**

1. Columns are renamed and formatted to `snake case`.
2. Columns with `int` data types such as `quantity` are filled with 0 when cell values are empty.
3. A `uid` column is created by concatenating all of the columns present in the data.
4. The data is then split into 2 dataframes, one that has all unique `uid` values and one that does not.
5. The dataframe that contains none unique uids is then aggregated such that the uids are then unique. The only thing that changes is the `quantity` columns as that is the variable of aggregation.
6. The aggregated dataframe is then put back with the other datframe.
7.  Data types are then enforced to be consistent with the nature.
8. The data is then exported to BigQuery using a `MERGE STATEMENT` and GCS a clean `parquet` file is sent to the `clean` subfolder with the `tmo_connectivity_sales` folder.
9. A `gold layer` table is then created using SQL sent as a bigquery job which further cleans up the sales data as well as joins the data with our `MSL`. This table is called `tmo_connectivity_sales_gold`.