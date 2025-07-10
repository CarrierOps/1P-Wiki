## Data Checklist For Dashboards & Client Facing Tools

✅ Tables powering the dashboard are `partitioned and clustered`

✅ Partitioned and clustered columns are the primary and secondary `filters` in the dashboard

✅ Calculated fields and business logic done primarily in `BigQuery` and `Python`

✅ The tables needed for a dashboard are concise`(Keep everything in one central table as much as possible)`

✅ Limited use of `Table Blend` in Looker


✅ Tables powering the dashboard are using only the `necessary columns`

✅ Tables powering the dashboard are pulling in the `necessary date ranges or amount of data`

✅ `Minimized use of scheduled queries` especially with complicated logic and large dataset. Orchestrate them with the `Data Eng team`.





