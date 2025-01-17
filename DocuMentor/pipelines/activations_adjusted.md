# Activations Adjusted Pipeline

## Summary
The pipeline aims to refined the activations dataset within our dataset.

## Cadence
Every Tuesday at ~12:30 pm EST right after the activations data comes in.



## Flowchart
WIP

## Key Details

1. This pipeline flags data within the dataset that is deemed a `B2B` transaction.
2. These values are flagged based on the following statistical metrics: `z score`, `skew coefficient`, and `mean-median percent difference` and the activation_count number being strictly above the threshold of `50`. The data is grouped by `year_month`,`partner_display_name`,`product_line` and `esri_city`.
3. Entries with `z score` above 3 or below -3 are flagged, entries with a `skew coefficient`   above 1 or below -1 are flagged, and values with a `mean-median percent difference`  above 75% are flagged.
4. Flagged entries are then replaced with the median activation count for the grouping.
5. The output from the `B2B` adjustment, then gets fed into the next stage which is the reallocation of activations.
6. Activations that esri_cities that are not found in our allocations file or come in as null, get redistributed to the esri cities that are currently getting covered/have allocations for.

