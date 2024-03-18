# Dev & Prod Layers

## Description
All of our main infrastructure are exists in 2 layers being `dev` and `prod`. The `prod` layer stands for production and is the layer that our infrastructure is using and is running on. All tables in BigQuery without the `dev` abbreviation is a `prod` table. The `dev` layer is very similar to the `prod` layer as it mirrors the `prod` layer for the most part. The reason the `dev` layer exists is that if we need to make changes/edits to our infrastructure we can do it to the `dev` layer without breaking anything in the `prod` layer which is currently running all of our infrastructure. Most of the work is done in the `dev` environment of any piece of infrastructure.


