# Summary
The ATT pipeline takes data from a Google Sheet and brings that data into BigQuery.

## Flowchart

```mermaid
flowchart TD
id0(Person In Charge Of Updating Google Sheet)
id00(Google Sheets)
id000(Google App Script)
id0000(New Data In GCS Bucket)
id0-->id00
id00 --> id000
id000 --> id0000
id0000-->id1

subgraph Mage Pipeline

id1(Import Data From GCS)
id2(Import Seen Weeks)
id3(Import ATT Location Mapping)
id4(Import SKU Mapping)
id5(Import ATT MSL)
id6(Import ATT Schema)


id7(Filter And Format Columns)
id1-->id7

id8(Filter Weeks)
id7--> id8
id2--> id8
id9(Map SKU And Location)
id8-->id9
id3-->id9
id4-->id9
id10(ATT Join MSL)

id9--> id10
id5--> id10

id11(ATT Validate Schema)
id10-->id11
id6-->id11

id12(BigQuery Snapshot)
id13(Append Seen Weeks To BigQuery)
id14(Append Sales Data To BigQuery)
id15(Export Sales Data To GCS)


id11-->id12
id11-->id13
id11-->id14
id11-->id15


end

```
## Extra Details In Flowchart
1. New sales data is manually added to a google sheet usually every Tuesday.
2. A google app script is used to extract the data from the plx trix to be stored in GCS as well as used to fire off the pipeline. Any new file added into the `raw` subfolders of the `sell-through` bucket is what is used to trigger a pipeline run.
3. Once the data is imported into the Mage pipeline, we then filter the columns such that all columns are in snake case i.e. snake_case and we are only selecting the columns that we actually need.
4. Once the new data from GCS is imported into the Mage pipeline, we also import the seen weeks of the activations data from the table `silver_layer.att_daily_sales_seen_weeks`. By doing this, we avoid we avoid duplicate records and make sure that each pipeline run contains new data 
5. Map SKU And Location  creates a dictionary of the form {'att_SKU_code': SKU}. The `phone` column is then added to data by mapping the `location_number` to `cp_id`.
6. The ATT sales data is then merged with the ATT MSL using a LEFT JOIN.
7. The data is then filtered by removing duplicate `cp_id` and removing null values in the `cp_id` column.
8. The schema and data types of the sales data are then validated.
9. A snapshot of the sales data is then taken.
10. The sales data is then appended to BigQuery
11. The seen weeks are also appended to BigQuery.
12. The sales data is also exported to GCS in the `clean` subfolder.

## Links Associated To The ATT Pipeline

### Google Cloud Storage(GCS)

Link: [Google Cloud Storage](https://console.cloud.google.com/storage/browser/sell-through/att_daily_sales?pageState=(%22StorageObjectListTable%22:(%22f%22:%22%255B%255D%22))&authuser=0&project=orbital-airfoil-393318&prefix=&forceOnObjectsSortingFiltering=false)

### BigQuery

Link: [Main Table](https://console.cloud.google.com/bigquery?referrer=search&authuser=0&project=orbital-airfoil-393318&ws=!1m5!1m4!4m3!1sorbital-airfoil-393318!2ssilver_layer!3satt_daily_sales&rapt=AEjHL4PAMMTnRDeY0yzTwqAM3HhXa11et6cM_qucPY7Guz45cI5yQR6gSTBhX_u4a55Hm17vvulXf1VL5vJfSJhOnKgGD_OXQlqdr-pTxJ7q5J0MfZRASUU&pli=1)

Link: [Seen Dates Table](https://console.cloud.google.com/bigquery?referrer=search&authuser=0&project=orbital-airfoil-393318&ws=!1m5!1m4!4m3!1sorbital-airfoil-393318!2ssilver_layer!3satt_daily_sales_seen_dates&rapt=AEjHL4PAMMTnRDeY0yzTwqAM3HhXa11et6cM_qucPY7Guz45cI5yQR6gSTBhX_u4a55Hm17vvulXf1VL5vJfSJhOnKgGD_OXQlqdr-pTxJ7q5J0MfZRASUU&pli=1)

Link: [Location Mapping](https://console.cloud.google.com/bigquery?referrer=search&authuser=0&project=orbital-airfoil-393318&ws=!1m5!1m4!4m3!1sorbital-airfoil-393318!2ssilver_layer!3satt_location_mapping&rapt=AEjHL4PAMMTnRDeY0yzTwqAM3HhXa11et6cM_qucPY7Guz45cI5yQR6gSTBhX_u4a55Hm17vvulXf1VL5vJfSJhOnKgGD_OXQlqdr-pTxJ7q5J0MfZRASUU&pli=1)

Link: [SKU Mapping](https://console.cloud.google.com/bigquery?referrer=search&authuser=0&project=orbital-airfoil-393318&ws=!1m5!1m4!4m3!1sorbital-airfoil-393318!2ssilver_layer!3ssku_code_mapping&rapt=AEjHL4PAMMTnRDeY0yzTwqAM3HhXa11et6cM_qucPY7Guz45cI5yQR6gSTBhX_u4a55Hm17vvulXf1VL5vJfSJhOnKgGD_OXQlqdr-pTxJ7q5J0MfZRASUU&pli=1)

Link: [ATT MSL](https://console.cloud.google.com/bigquery?referrer=search&authuser=0&project=orbital-airfoil-393318&ws=!1m5!1m4!4m3!1sorbital-airfoil-393318!2ssilver_layer!3satt_msl&rapt=AEjHL4PAMMTnRDeY0yzTwqAM3HhXa11et6cM_qucPY7Guz45cI5yQR6gSTBhX_u4a55Hm17vvulXf1VL5vJfSJhOnKgGD_OXQlqdr-pTxJ7q5J0MfZRASUU&pli=1)


### Google Sheets

Link:[Google Sheet For Sales Data](https://docs.google.com/spreadsheets/d/1CO9w8Ur9g4Y_BEhHzq715wiJ1t8LFhF9op_rYfwcT4s/edit#gid=225119370)
