# GFA Gold And Platinum Table Pipeline

## Summary
This pipeline creates all of the gold and platinum GFA tables. 

## Cadence
This pipeline fires immediately after the `gfa_silver` pipeline finishes running.


## Flowchart


```mermaid
flowchart TD
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

id1[[GFA Accessories]]
id2[[GFA Inv]]
id3[[GFA Lv]]
id4[[GFA Merch]]
id5[[GFA Notes]]
id6[[GFA OOS]]
id7[[GFA Promo]]
id8[[GFA Visits]]
id9[[GFA ALL]]

id1-->id2-->id3-->id4-->id5-->id6-->id7-->id8-->id9


```

## Extra Detail In FLowchart

1. All of these blocks are using SQL to create table within BigQuery. No data is imported or export. These blocks simply instruct BigQuery to perform tasks using SQL.
2. The team can write what they want to do using SQL, and have them directly orchestrated in Mage.


