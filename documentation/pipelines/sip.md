# SIP (Spiff, incentive, and promo )

## Summary

This pipeline grabs data from the `Promo, Spiff, and Incentive Tracking` google sheet to bring it in BigQUery in the `sip` table.

## Cadence

**Wednesday 8am PST (every week)**

The google app script runs on a schedule. Once finished running, it'll the next step in the flowchart, which will trigger the next step and so one - the rest of the flowchart is event-driven.

## FlowChart

```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#0277bd',
      'primaryTextColor': '#ffffff',
      'primaryBorderColor': '#b38481',
      'lineColor': '#E2E2E2',
      'secondaryColor': '#9e91c9',
      'tertiaryColor': '#5c8a8a',
      'tertiaryTextColor': '#ffffff',
      'tertiaryBorderColor': '#b38481'
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

## Relevant links

### Google Cloud Storage (GCS)

[Sip data](https://console.cloud.google.com/storage/browser/deep-dive/SIP-tracking-resources/raw?pageState=(%22StorageObjectListTable%22:(%22f%22:%22%255B%255D%22))&authuser=1&project=orbital-airfoil-393318&prefix=&forceOnObjectsSortingFiltering=false)

### BigQuery

[sip table](https://console.cloud.google.com/bigquery?referrer=search&authuser=1&project=orbital-airfoil-393318&ws=!1m25!1m4!1m3!1sorbital-airfoil-393318!2sbquxjob_43604433_18e350ef607!3sUS!1m4!1m3!1sorbital-airfoil-393318!2sbquxjob_4ee7cd63_18e3520580e!3sUS!1m4!4m3!1sorbital-airfoil-393318!2ssilver_layer!3sactivations!1m4!1m3!1sorbital-airfoil-393318!2sbquxjob_e61dcd5_18e351ff1c7!3sUS!1m4!4m3!1sorbital-airfoil-393318!2ssilver_layer!3ssip)

### Google App Script

[SIP Source Export](https://script.google.com/u/0/home/projects/1TrYmwmtMBE0q2hQZRRbW_vyxlAKbyHzyX4dGvkJYdhCYOd5dvxKVHzej/edit)
