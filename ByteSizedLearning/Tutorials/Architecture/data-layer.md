 # Data Layer
 
 Our data and tables in BigQuery are structured in into the following layers: `silver_layer`, `gold_layer`, and `platinum_layer`. Each tier represents a specific classification of data. **Note:** There is a `bronze` layer, but that only exists in Google Cloud Storage(GCS) and that is where all of our raw data is stored.

**silver_layer:** This layer takes the data from the `bronze` and transforms/cleans it such that it is accurate and easily queryable in BigQuery.

**gold_layer:** This layer aggregates, joins, filters, etc the tables in the `silver_layer` to power and create dashboards, and data driven reporting tools to be used by various stakeholders and field/sales personnel.

**platinum_layer:** This layer will be composed of highly summarized and aggregated data that will be easily presentable to all stakeholders.

**_Important Note:_** All of our actively used tables will **not** have the `dev` abbreviation. The `dev` abbreviation stands for developer which is primarily used by the development team for testing purposes.