# GFA Master Data

## Summary
The gfa_master_data pipeline takes survey directly from salesforce that is connected to 4 tabs in a google sheets, and ingests that data into our database.

## Flowchart
WIP

# Key transformations

- Reformat column names to snake case.
- `Survey_responses` is `LEFT JOINED` with `survey_with_sva` on `survey_response_id` and then `LEFT JOINED` with `sva_with_visit_id` on `store_visit_activity_id`. This generates the table `gfa_master_data`.
- The other table uses just the 4th tab called `visit_data`.
- Data types are then enforced and then exported to BigQuery.
