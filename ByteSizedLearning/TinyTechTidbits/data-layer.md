# Data Layer

To enhance the efficiency, reliability, and accessibility of our data, we've adopted a layered architecture (also called medallion architecture) within our data infrastructure. This architecture divides our data into four distinct layers: bronze, silver, gold, and platinum. Each layer represents a different stage in the data's lifecycle, from raw ingestion to refined analytics-ready datasets. This structured approach ensures that our data is managed, processed, and utilized effectively to support reporting, analytics, and decision-making processes.

By organizing data processing into distinct layers, the medallion architecture significantly simplifies maintenance and enhances flexibility. This clear structure allows for targeted updates and optimizations without disrupting the entire data ecosystem, making it easier to adapt to changing business requirements. Such segmentation ensures that data governance is more straightforward, as each layer can be individually managed and secured. This approach not only streamlines the upkeep of the data infrastructure but also empowers us to rapidly respond to new opportunities or challenges, effectively leveraging data as a strategic asset.

<figure align="center">
    <img src="../../imgs/Organization of data - GCP infra (2).png" width="95%">
  <figcaption>Overview of the Medallion Architecture and where each layer is hosted.</figcaption>
</figure>

## Bronze Layer (Raw Data)

The bronze layer is the foundation of our data architecture, acting as the initial repository for raw data. Data in this layer is collected from various sources, including surveys (e.g., GFA, S123), reference files (e.g., MSL, location mappings), and other external or internal data streams. At this stage, data remains in its original form, untouched and unprocessed, ensuring that we have a faithful capture of the source information for auditing, traceability, and compliance purposes.

Data in this layer lives entirely in our data lake on [GCS](https://github.com/CarrierOps/1P-Wiki/blob/main/DocuMentor/gcp/GCS/bucket_description.md)

## Silver Layer (Cleaned/Curated Data)

Data progresses to the silver layer after undergoing initial cleaning and curation processes. Here, we perform essential quality checks, remove duplicates, correct errors, and standardize formats. This layer serves as a centralized repository for cleaned data that is harmonized from different sources, making it more reliable and consistent for further processing. The aim is to create a trusted & reliable dataset that serves as the base for any reporting & analytics.

Data in this layer primarily in [BigQuery](https://github.com/CarrierOps/1P-Wiki/blob/main/DocuMentor/gcp/BigQuery/bigquery.md), but a copy of the cleaned data is also stored in the data lake for archiving

## Gold Layer (Modeled, Transformed, Aggregated Data)

The gold layer represents a significant transformation from cleaned data to analytics-ready information. In this stage, data is joined, aggregated, enriched, and transformed to support specific analytical models and reporting needs. It involves creating detailed views, summaries, and dimensional models that facilitate deep analysis and insights. The gold layer is where complex business logic is applied, turning data into valuable information that directly supports decision-making processes.

Data in this layer lives entirely in BigQuery.

## Platinum Layer (Presentation-Ready Data)

The platinum layer is a subset of the gold layer, specifically tailored for end-user consumption. This layer includes data that is ready to be exposed to the rest of the team, clients, or external stakeholders. It is highly curated and often includes dashboards, visualizations, and reports that are directly used in presentations, decision support systems, and external publications. The platinum layer is characterized by its ease of access, high relevance, and alignment with business objectives, ensuring that users can quickly derive insights and make informed decisions.

Data in this layer lives in BigQuery. It's worth noting that we could consider dashboards, reports, etc as being part of this layer.

<!--
 ## Description

 Our data and tables in BigQuery are structured in into the following layers: `silver_layer`, `gold_layer`, and `platinum_layer`. Each tier represents a specific classification of data. **Note:** There is a `bronze` layer, but that only exists in Google Cloud Storage(GCS) and that is where all of our raw data is stored.

**silver_layer:** This layer takes the data from the `bronze` and transforms/cleans it such that it is accurate and easily queryable in BigQuery.

**gold_layer:** This layer aggregates, joins, filters, etc the tables in the `silver_layer` to power and create dashboards, and data driven reporting tools to be used by various stakeholders and field/sales personnel.

**platinum_layer:** This layer will be composed of highly summarized and aggregated data that will be easily presentable to all stakeholders.

**_Important Note:_** All of our actively used tables will **not** have the `dev` abbreviation. The `dev` abbreviation stands for developer which is primarily used by the development team for testing purposes. -->
