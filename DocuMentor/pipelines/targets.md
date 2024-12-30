# Target Setting Pipeline

## Summary 
The pipeline automates the manual work of the target setting process. A process usually taking 10-12 hours per month across various members now reduced down to mere minutes.


## Cadence
Monthly -> Whenever forecast sales data comes in.


## Overview Of Process

1. The current year + quarter share is based on the last year's quarter.
2. The `group share` is calculated by taking the total amount sold from last year's quarter for each product(`group total`), and dividing that into the total amount sold for each product in each store(or city). The total of all the group shares for each product  must sum to 1 as it is just splitting the % sold across various difference stores/cities
3. The group shares then get multiplied into the total quarter forecast(The numbers we want to hit basically) to get quarterly level targets for each product+store(or city) combination.
4. We then increase the granularity of the quarterly level targets by multiplying the quarterly level targets by a `week share`.
5. The` week_share` is targets that account for every week within the quarter.This number is also a decimal and must add up to 1 for the quarter.
6. The `week_share` is calculated very similar to the `group_share` as we sum the total number forecasted sales for quarter+carrier+product and divide that into the sales number projected for each week.

