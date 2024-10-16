# How To Trigger Pipelines

WIP -> More to come!!!!

## TMO Pipelines

***TMO Mobile One Sales:***

- Data gets added to a google sheet from the dealer.
- Triggered from a google app script.
- Set to run `every Tuesday at ~9-10am EST`.
- To manually trigger, run the `TMOM1SALESPULL`.


***TMO Mobile One Inventory:***
- Data gets added to a google sheet from the dealer.
- Triggered from a google app script.
- Set to run `every Tuesday at ~9-10am EST`.
- To manually trigger, run the `TMOM1INVPULL`.


***TMO GP Mobile Sales:***

- Data gets sent via email in `csv` format.
- To trigger(**for now**), download the `sales` csv and then rename the file as follows: `TMOGPSALES - mm.dd.yyyy - raw.csv`. As an exmaple, at the time of writing this, the day is `10/10/2024`, therefore the file name should be `TMOGPSALES - 10.10.2024 - raw.csv`.
- To trigger the pipeline, place this file into a bucket called `the-beach-stg`.
- This data is provided to us with very consistent formatting, so usually no intervention aside from changing the name of the file is needed.

***TMO GP Mobile Inventory:***
- Data gets sent via email in `csv` format.
- To trigger(**for now**), download the `inventory` csv and then rename the file as follows: `TMOGP Inventory - mm.dd.yyyy - raw.csv`. As an exmaple, at the time of writing this, the day is `10/10/2024`, therefore the file name should be `TMOGP Inventory - 10.10.2024 - raw.csv`.
- To trigger the pipeline, place this file into a bucket called `the-beach-stg`.
- This data is provided to us with very consistent formatting, so usually no intervention aside from changing the name of the file is needed.

***TMO GP Mobile Inventory Summary:***
- Data gets sent via email in `csv` format.
- To trigger(**for now**), download the `inventory summary` csv and then rename the file as follows: `TMOGPSUM Inventory - mm.dd.yyyy - raw.csv`. As an exmaple, at the time of writing this, the day is `10/10/2024`, therefore the file name should be `TMOGPSUM Inventory - 10.10.2024 - raw.csv`.
- To trigger the pipeline, place this file into a bucket called `the-beach-stg`.
- This data is provided to us with very consistent formatting, so usually no intervention aside from changing the name of the file is needed.


***TMO Connectivity Source Sales:***
- Data gets sent via email in `xlsx` format.
- To trigger(**for now**), download the `sales` tab of the excel file to a `csv` file.
- Make sure that no columns are missing from the data (**the data sent is sometimes inconsistent**).
- Format the `sku code` column to a number i.e. no scientific notation.
- Format the `msrp` column(**must be integer**) such that it's just an integer i.e.(no $ or , in the cells)
- Rename the file as follows: `TMOCON Sales Data - mm.dd.yyyy - raw.csv`.As an exmaple, at the time of writing this, the day is 10/10/2024, therefore the file name should be
`TMOCON Sales Data - 10.10.2024 - raw.csv`.

- To trigger the pipeline, place this file into a bucket called `the-beach-stg`.


***TMO Connectivity Source Inventory:***
- Data gets sent via email in `xlsx` format.
- To trigger(**for now**), download the `inventory` tab of the excel file to a `csv` file.
- Make sure that no columns are missing from the data (**the data sent is sometimes inconsistent**).
- Format the `sku code`, `Delivery Order`, `STO` and `Serial Number` columns to a number i.e. no scientific notation.

- Rename the file as follows: `TMOCON Inventory - mm.dd.yyyy - raw.csv`.As an exmaple, at the time of writing this, the day is 10/10/2024, therefore the file name should be
`TMOCON Inventory - 10.10.2024 - raw.csv`.

- To trigger the pipeline, place this file into a bucket called `the-beach-stg`.



***TMO Wireless Vision Sales:***
- Data gets sent via email in `xlsx` format.
- To trigger(**for now**), download the `sales` tab of the excel file to a `csv` file.
- Format the `sku code`,`imei`, and `employee number` columns to a number i.e. no scientific notation.
- Make sure the `msrp` column is still a `float`(**keep format the same**) but ensure that there are no commas in the cells.
- Rename the file as follows: `TMOWV Sales - mm.dd.yyyy - raw.csv`. As an exmaple, at the time of writing this, the day is 10/10/2024, therefore the file name should be `TMOWV Sales - 10.10.2024 - raw.csv`.
- To trigger the pipeline, place this file into a bucket called `the-beach-stg`.

***TMO Wireless Vision Inventory:***
- Data gets sent via email in `xlsx` format.
- To trigger(**for now**), download the `inventory` tab of the excel file to a `csv` file.
- Rename the file as follows: `TMOWV Inventory - mm.dd.yyyy - raw.csv`. As an exmaple, at the time of writing this, the day is 10/10/2024, therefore the file name should be `TMOWV Inventory - 10.10.2024 - raw.csv`.
- To trigger the pipeline, place this file into a bucket called `the-beach-stg`.



