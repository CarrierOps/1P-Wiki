# Cron expressions

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
