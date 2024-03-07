m
# Us Activations Pipeline Documentation

## Summary
The US activations pipeline takes data from a Google Plx Trix and brings that data into BigQuery. The the pipeline itself is shared with the CA activations as the data structure and type of data is essentially identical.

## Flowchart

```mermaid
flowchart TD
id0(Google Plx Trix)
id00(Google Sheets)
id000(Google App Script)
id0000(New Data In GCS Bucket)
id0-->id00
id00 --> id000
id000 --> id0000
id0000 -->id1

subgraph Mage Pipeline
id1(Import Data From GCS)
id2(Import State Names From BQ)
id3(Import Seen Weeks From BQ)
id4(Import Esri City From BQ)
id5(Filter By Seen Weeks)
id1 --> id5
id3 --> id5
id6(Aggregate Data Up to City Level)
id5 --> id6
id7(Create Google City And uid columns)
id6 --> id7
id2 --> id7
id8(Map Google City To Esri City)
id7 --> id8
id4 --> id8
id9(Validate Schema And Data Types)
id8 --> id9
id10(BigQuery Snapshot)
id9 --> id10
id11(Add Seen Weeks to BQ)
id10 --> id11
id12(Export To GCS)
id13(Append To BigQuery)
id10 --> id12
id10 -->id13
end

```

## Extra Details In Flowchart
WIP

Be sure to mention how the uid is created,
Any joins,
Any filters,
etc

