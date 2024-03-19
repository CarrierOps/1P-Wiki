# Cloud Scheduler

It a GCP service that allows you to run jobs on a schedule. It uses [CRON syntax](#cron-syntax) to set the schedule. When configuring it, you can chose how you want it to execute - choose what happens at the set schedule. You can choose to send an [HTTP](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/TinyTechTidbits/HTTP.md) request, publish a message to a Pub/Sub topic, or do other things (not relevant for our infrastructure). Some more details:

- For HTTP jobs, you can send POST, GET, HEAD, PUT, DELETE, PATCH, OPTIONS requests
- For HTTP jobs, you can send a data payload
- For HTTP jobs, you can send Auth headers to authenticate if you need to make a request to a secured API
  - OAuth & OIDC
- For Pub/Sub jobs, you can specify the content of the message published to the selected topic

## CRON-syntax

Syntax used for time-based scheduled jobs in UNIX (think Linux or Apple's OS x). They are typically called `cron jobs`, which are defined by a `cron expression`.

`cron expressions` are a string composed of 5 or 6 fields separated by spaces. So a typical cron job look like this: `* * * * *`. Each field represents a time dimension. So (listing the fields from left to right as they appear in the cron-expression):

1. Minute (0-59)
2. Hour (0 -23)
3. Day of the month (1 - 31)
4. Month (1 - 12 or Jan - Dec)
5. Day of the Week (0 - 6 or Sun - Sate), 0 is Sunday
6. (optional) Year

Each field has a specific value range (specified above in the parentheses). Using this syntax, we can build cron-expressions that will run cron-jobs on the defined schedule.

There are also special character that can be used in cron-jobs such as:

- Asterisk (\*): Represents "every" possible value for a field. For example, an asterisk in the hour field would be every hour.
- Comma (,): Allows you to specify a list of values for a field. For instance, using 1,3,5 in the day-of-week field means Monday, Wednesday, and Friday.
- Hyphen (-): Specifies a range of values. If you write 1-5 in the day-of-week field, it means Monday through Friday.
- Slash (/): Specifies increments. \*/15 in the minutes field means "every 15 minutes".

Some examples:

- `* * * * *`: run every minute, every day, every month
- `0 8 * * *`: Run every day at 8am
- `0 8 * * 1-5`: Run at 8am Monday through Friday
- `*/15 * * * *`: runs every 15 mins every day of every month
- `30 9-17 * * 1-5`: Run at the half-hour mark every Monday through Friday between the hours of 9am and 5pm
- `*/15 8-11 * * Wed`: Runs every 15 minutes between the hours of 8am and 11am every Wednesday
- `0-30/10 * * * 1-5` Runs every 10th minute from the 0th to the 30th minute of every hour Monday through Friday
