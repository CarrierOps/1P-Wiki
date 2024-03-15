# Google Cloud Storage


## GCS Bucket File Structure
```
    Google-carrier-data-infra
    ├──── 1p-advocacy/
    │     └── fall_2023/
    ├──── 1P-msl/
    ├──── activationz/
    │     └──CA_wkly/
    │        └── raw/
    │        └── clean/
    │     └──US_wkly
    │        └── raw/
    │        └──clean/
    │     └──resources  
    │──── cloud-functions-deployments/
    │──── deep-dive
    │     └──SIP-tracking-resources
    │        └── raw/
    │──── drift-wood/
    │──── gcf-v2-sources-788520541806-us-west1/
    │     └── bq_silver_sync/
    │     └── csv-to-parquet/
    │     └── data-backup-sync/
    │     └── data-backup/
    │     └── dispatcher-ppln/
    │     └── outflow_ppln/
    │     └── trigger_att_sales_silver_ppln/
    │     └── trigger_bby_ca_silver_ppln/
    │     └── trigger_bby_us_silver_ppln/
    │     └── trigger_ca_bby_silver_ppln/
    │     └── trigger_gfa_silver_ppln/
    │     └── trigger_sip_silver_ppln/
    │     └── trigger_us_bby_silver_ppln/
    │     └── trigger_wkly_acts_ppln/
    │──── gcf-v2-uploads-788520541806-us-west1/
    ├──── gfa_data/
    │     └── raw/
    │     └──clean/
    ├──── infra-data-backups/
    │     └── BigQuery/
    │     └── GCS/
    │     └── Scripts/
    │──── lake-outflow/
    │──── lake-outflow-stg/
    │──── mage-app/
    │     └── logs/
    │         └── dwh_pplns/
    │             └── piplines
    │                 └── activations_silver/
    │                 └── att_sales_silver
    │                 └── bby_ca_silver
    │                 └── bby_us_silver
    │                 └── gfa_data_silver/
    │                 └── sip_silver/
    │                 └── wkly_activations_silver/
    │──── sell-through
    │      └── att_daily_sales/
    │          └── raw
    │          └── clean
    │          └── supporting_files
    │     └── bby_sellout
    │          └── ca
    │              └── raw
    │              └── clean
    │          └── us
    │              └── raw
    │              └── clean
    │──── supporting-file/
    │──── tf-infra-states/
    │
    │──── the-beach/
    │──── the-beach-stg/
    │
    │
    │       
    └─

```

