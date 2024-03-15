# GCS Bucket Description

## 1p-advocacy

- This bucket stores the `Google 1P Advocacy` survey data.

## 1p-msl

- This bucket stores snapshots of the cleaned version of the `Google 1P MSL` google sheet.
- The data is exported from the `msl` pipeline to this bucket.

## activationz

- This bucket stores all of the weekly activations sales data.
- The bucket has subfolders `ca` and `us` indicating which coutry is the sales data referring.
- The `raw` subfolders indicate that the data is coming from the `Google 1P Sellout And Activations Data` google plx trix.
- The `clean` subfolders indicate that the data is being exported from the `activations` pipeline.

## cloud-functions-deployments

- Confirm with Thomas
- This bucket stores all of the cloud functions that are used for our entire infrastructure.
- An example of where we use cloud functions are in the majority of our data pipelines

## deep-dive

- This bucket stores all of the raw data from the `Promo, Spiff, and Incentive Tracking` google sheet.

## drift-wood
* Works with dispatcher pipeline
* If there is no match from the dispatcher pipeline, the file will go to this bucket.

## gcf-v2-sources-788520541806-us-west1
* Google managed version of cloud functions deployment.
* Allows you to see source code of the cloud function.

## gcf-v2-uploads-788520541806-us-west1
* Google managed bucket to hold code.


## gfa_data

- This bucket stores all of the daily GFA data.
- The `raw` subfolder indicates that the data is coming from the `Google 1P SF GFA Data` google plx trix.
- The `clean` subfolder indicates that the data is being exported from the `gfa` pipeline.

## infra-data-backups

- This bucket stores weekly backups of all the tables in BigQuery as well as a backup copy of all of our scripts such as the Google App Scripts used in our pipelines.

## lake-outflow

- This is the destination bucket for files that have been placed into the `lake-outflow-stg` bucket.

## lake-outflow-stg

- When a `parquet` file is placed into this bucket, that file will be converted to a `csv` and be placed into the `lake-outflow` bucket.

## mage-app

- This bucket contains logs pertaining to all of our `mage` pipelines.

## sell-through

- The bucket contains all of the sales data from Best Buy and ATT.
- The folder labelled `bby_sellout` contains only BBY sales data and contains folders for `ca` and `us` data.
- Like in other buckets, the `ca` and `us` subfolders are split into `raw` and `clean` subfolders where the `raw` data comes form the `Google 1P Sellout And Activations Data` google plx trix and the `clean` data comes from the BBY pipeline.
- The folder labelled `att_daily_sales` contains only att sales data and is split into `raw` and `clean` subfolders.

## supporting-file
* Stores supporting material from the program.
* Maybe store historical data down the road.

## tf-infra-states
* https://opentofu.org/docs/intro/
* Link documentation maybe?
* We're terraforming mars.
* Complicated



## the-beach

- This bucket is the destination bucket for `the-beach-stg` bucket.
- The primary purpose of this bucket is to trigger the `dispatcher` cloud function which places parquet files into the correct location in GCS.

## the-beach-stg

- The bucket converts `csv` files placed into it into `parquet` files that will are to be placed into `the-beach` bucket.
