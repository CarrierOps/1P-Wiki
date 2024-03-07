
# MSL Pipeline Documentation

## Summary
The MSL pipeline has 2 primary purposes. The first purpose is to have an up to data MSL in available in BigQuery. The second purpose is to track changes made to the MSL over time.


## Flowchart

```mermaid
flowchart TD
id1(Import MSL From BigQuery)-->id2(Transform And Clean BigQuery MSL)
id3(Import MSL From Google Sheets)--> id4(Transform And Clean MSL From Google Sheets)
id2--> id5(Compare Both MSL)
id4 -->id5
id6(Delete From Live Payload)
id7(Append To Historical Payload)
id8(Append New Records To Live Payload)
id9(Update Records In Live Payload)


id5--> id6
id5-->id7
id5--> id8
id5-->id9

id2-->id6
id2-->id7

id4-->id8
id4-->id9

id6--> id10(Delete Records From Live Table In BQ)
id7--> id11(Append Records To Historical Table In BQ)

id12(Update And Insert aka Upsert Payload)
id8-->id12
id9-->id12

id12--> id13(Upsert To Live Table in BQ)


```
## Extra Details In Flowchart
WIP -> Will do once pipeline is finalized.




## Links Associated To The MSL Pipeline

### BigQuery
Link: [Up to date MSL](https://console.cloud.google.com/bigquery?referrer=search&authuser=0&project=orbital-airfoil-393318&ws=!1m5!1m4!4m3!1sorbital-airfoil-393318!2ssilver_layer!3smsl&rapt=AEjHL4P2Aj3Y_3y1lr9qjXMkE81QjHY1rnPyy4fSUwgdCq-kZxQ0eVvXh6B5msvwDWyBpmXY1OatLBl-_UhelmLO-0yf5_EmwNwVLIrCvqetfkngIwSIWV8)

The Table reference in BQ is `silver_layer.msl`

Link: [Historical Changes MSL](https://console.cloud.google.com/bigquery?referrer=search&authuser=0&project=orbital-airfoil-393318&ws=!1m5!1m4!4m3!1sorbital-airfoil-393318!2ssilver_layer!3smsl_historical&rapt=AEjHL4P2Aj3Y_3y1lr9qjXMkE81QjHY1rnPyy4fSUwgdCq-kZxQ0eVvXh6B5msvwDWyBpmXY1OatLBl-_UhelmLO-0yf5_EmwNwVLIrCvqetfkngIwSIWV8)

The Table reference in BQ is `silver_layer_historical`



### MSL Google Sheet
Link: [MSL Google Sheet](https://docs.google.com/spreadsheets/d/1g_R4e28nAeWWPMXmLJAhQNEvxdVL8B00wfMLKMoGBjw/edit?pli=1#gid=1385454884)
