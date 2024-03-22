# Cloud Scheduler Documentation

## Overview

While we try to keep things as event driven as possible, there is still a need for scheduled workflows (whether that be the kick off a workflow that is event driven, or to run scripts that perform routine tasks like clean up our datalake). For more in-depth explanation of Cloud Scheduler, [check out this documentation](https://github.com/CarrierOps/1P-Wiki/blob/main/ByteSizedLearning/Description%20Of%20Services/Scheduler.md).

## List of Resources

**Note**: Pay attention to timezones, it's super confusing...

* **arcgis-gcs-pull**
  * **Cadence**: Every Monday at 8am UTC+0 (London, England time, so 1am Pacific time right now, and at midnight when it's daylight savings ).
  * **description**: This scheduler has a pubsub target type. It sends a message to the [arc-gis-topic](https://github.com/CarrierOps/1P-Wiki/blob/main/DocuMentor/gcp/PubSub/pubsub.md) topic.
* **data_backup_scheduler**
  * **Cadence**: Every Friday at 4pm UTC+0 (so 8am Pacific time during daylight savings, and 9am otherwise).
  * **description**: This scheduler has a pubsub target type. It sends a message to the [data_backup_topic](https://github.com/CarrierOps/1P-Wiki/blob/main/DocuMentor/gcp/PubSub/pubsub.md) topic.
