## Data Checklist For Dashboards & Client Facing Tools

✅ Tables powering the dashboard are `partitioned and clustered`

✅ Calculated fields and business logic done primarily in BigQuery or MAGE

✅ The tables needed for a dashboard are concise`(Keep everything in one central tables as much as possible)`

✅ Limited use of `Table Melt` in Looker


✅ Tables powering the dashboard are using only the `necessary columns`

✅ Tables powering the dashboard are pulling in the necessary date ranges or amount of data

✅ Minimized use of scheduled queries especially with complicated logic and large dataset. Orchestrate then with the Data Eng team.





