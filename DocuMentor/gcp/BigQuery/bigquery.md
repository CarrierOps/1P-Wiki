# BigQuery Structure

BigQuery is the star of the show. It is where all data used for reporting, dashboard, analytics, etc is stored. It is where all raw data ends up after being cleaned, refined, aggregated, transformed, and modeled.

It houses silver, gold, and platinum layer data. You can [check out this documentation](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/TinyTechTidbits/data-layer.md) for more details on the different layers of data.

<!-- Our data and tables in BigQuery are structured in into the following layers: `silver_layer`, `gold_layer`, and `platinum_layer`. Each tier represents a specific classification of data. **Note:** There is a `bronze` layer, but that only exists in Google Cloud Storage(GCS) and that is where all of our raw data is stored.

**silver_layer:** This layer takes the data from the `bronze` and transforms/cleans it such that it is accurate and easily queryable in BigQuery.

**gold_layer:** This layer aggregates, joins, filters, etc the tables in the `silver_layer` to power and create dashboards, and data driven reporting tools to be used by various stakeholders and field/sales personnel.

**platinum_layer:** This layer will be composed of highly summarized and aggregated data that will be easily presentable to all stakeholders.

**_Important Note:_** All of our actively used tables will **not** have the `dev` abbreviation. The `dev` abbreviation stands for developer which is primarily used by the development team for testing purposes. -->

## Active Tables In BigQuery

**Please visit the following link to see all of our actively used and updated tables in BigQuery.**

[1P BQ Tables & Dashboards](https://docs.google.com/spreadsheets/d/1549_qrfdXPvEd39EZHzbHeqEhG94Ez88WP836dVeUnk/edit#gid=0)

## Commonly Used Queries

[ATT Total Sales By Day](https://console.cloud.google.com/bigquery?sq=788520541806:cfd6850f224049759ce7b1e577311785)

[BBY Weekly Sales](https://console.cloud.google.com/bigquery?sq=788520541806:42d3b905b6d94adbb991848f6ea4546f)

[Total Weekly Activations](https://console.cloud.google.com/bigquery?sq=788520541806:83ccfd14949d43c6beda3d9f5d3973bf)

[MSL Deleted Store IDs](https://console.cloud.google.com/bigquery?sq=788520541806:414a0846c8cf4a42b9c27531d06f4979)

[MSL Stores that have had a change made to them](https://console.cloud.google.com/bigquery?sq=788520541806:d11ee173992941ba86122de21d6d1f72)
