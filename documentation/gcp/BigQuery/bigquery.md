notes: silver, gold, plat etc
dev vs prod
Links to wiki
Used Table names -> Link to catalog sheet
connections between different services

# BigQuery Structure
Our data and tables in BigQuery are structured in into the following layers: `silver_layer`, `gold_layer`, and `platinum_layer`. Each tier repesents a specific classification of data. **Note:** There is a `bronze` layer, but that only exists in Google Cloud Storage(GCS) and that is where all of our raw data is stored.

**silver_layer:** This layer takes the data from the `bronze` and transforms/cleans it such that it is accurate and easily queryable in BigQuery.

**gold_layer:** This layer aggregates, joins, filters, etc the tables in the `silver_layer` to power and create dashboards, and data driven reporting tools to be used by various stakeholders and field/sales personel.

**platinum_layer:** This layer will be composed of highly summarized and aggregated data that will be easily presentable to all stakeholders.

***Important Note:*** All of our actively used tables will **not** have the `dev` abbrevation. The `dev` abbreviation stands for developer which is primarily used by the development team for testing purposes.




# Active Tables In BigQuery

**Please visit the following link to see all of our actively used and updated tables in BigQuery.**

[1P BQ Tables & Dashboards](https://docs.google.com/spreadsheets/d/1549_qrfdXPvEd39EZHzbHeqEhG94Ez88WP836dVeUnk/edit#gid=0)


