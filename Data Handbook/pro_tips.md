# Pro Tips 🏅

**Pro Tip 1:** If you have a lot of columns, it is probably worth unpivoting the data to convert to `long format`. This could help reduce the cost of the queries associated with your table or tool. `Unpivoting to long format is highly useful for survey data with a lot of questions as columns!`

**Pro Tip 2:** Using `limit` to reduce the number of rows in the output of a query `DOES NOT CHANGE THE AMOUNT OF DATA PROCESSED!`. A full table scan will be done regardless if you select * with a limit or no limit. The only thing that will change are the number of rows in the output. `Filtering with partitioned and clustered columns, aggregation, and selecting less columns are what really reduce data usage`.

**Pro Tip 3:** The more clever you are with how you partition and cluster your dashboards, the more efficient you'll be! `Create a dashboard with the partitioned and clustered columns in mind`.


**Pro Tip 4:** `Create what the end user wants to see and cares about!` Often times tools get overengineered for minimal benefit since the end user really only cares about a specific  set of data or pieces of information. If the user wants a skateboard give them a skateboard, not a Lamborghini Huracan. `Being clear, concise and succinct is usually the best way to convey information in a effective way`. `Can the end user clearly and easily take away the information they need?`