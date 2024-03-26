# Cloud Scheduler

It a GCP service that allows you to run jobs on a schedule. It uses [CRON syntax](#cron-syntax) to set the schedule. When configuring it, you can chose how you want it to execute - choose what happens at the set schedule. You can choose to send an [HTTP](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/TinyTechTidbits/HTTP.md) request, publish a message to a Pub/Sub topic, or do other things (not relevant for our infrastructure). Some more details:

- For HTTP jobs, you can send POST, GET, HEAD, PUT, DELETE, PATCH, OPTIONS requests
- For HTTP jobs, you can send a data payload
- For HTTP jobs, you can send Auth headers to authenticate if you need to make a request to a secured API
  - OAuth & OIDC
- For Pub/Sub jobs, you can specify the content of the message published to the selected topic

## CRON-syntax

See [this document](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/TinyTechTidbits/cron-expressions.md) for more in depth explanation of CRON
