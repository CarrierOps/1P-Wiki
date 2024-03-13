# SIP (Spiff, promo, and incentive)

## Summary

This pipeline grabs data from the `Primo, Spiff, and Incentive Tracking` google sheet to bring it in BigQUery in the `sip` table.

## Cadence

Wednesday 8am PST (every week)

The google app script runs on a schedule. Once finished running, it'll the next step in the flowchart, which will trigger the next step and so one - the rest of the flowchart is event-driven.

## FlowChart

```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#0277bd',
      'primaryTextColor': '#ffffff',
      'primaryBorderColor': '#e0bbff',
      'lineColor': '#a2a2a2',
      'secondaryColor': '#3f51b5',
      'tertiaryColor': '#5c8a8a',
      'tertiaryTextColor': '#ffffff'
    }
  }
}%%
---
title: Node
---
flowchart TD
    id0([source sheet])
    id1[GCS Bucket]
    id5[(SIP table)]

    id0 -- SIP Source Export --> id1

    subgraph Mage-pipeline
        id2[[clean data]]
        id3[[validate data]]
        id4[[Write to BigQuery]]

        id2 --> id3
        id3 --> id4
    end

    id1 --> Mage-pipeline
    id4 --> id5
```

## More Details

1. The Google App Script is set up to pull data from the source sheet. It itterates through all Carrier worksheets in order. The script uplaods the data to GCS - each carrier worksheet is uploaded as an individual file
   * the order is of the carrier worksheets is specified as an array in the app script, and is **VERY** **VERY** important to not change (or to make sure VZW stays as the last item in that array)
2. Once data is dropped in the 'deep-dives' bucket in the 'sip' subfolder, the Mage pipeline is triggered, and reads the files for all carriers.
3. Each file is cleaned
   1. columns are renamed
   2. special characters are removed
   3. Nulls & N/As are mapped
   4. price columns are formated 
   5. Price cols are converted to floats
4. The cleaned data's schema is validated against the BigQuery table's schema
5. The table in BigQuery is entirely replaced with the new batch of data
