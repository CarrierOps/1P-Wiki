# dispatcher-ppln

## Summary

This pipeline grabs files from `the-beach` bucket and drops it into the appropriate bucket within the data lake. It uses 2 files - bucket_dispatch.json & folder_dispatch.json to match key words within the source file name with the destination bucket/folder.



## Diagram

<figure align="center">
    <img src="../../../imgs/dispatcher ppln.png" width="95%">
  <figcaption>High-level diagram showing the how dispatcher-ppln Cloud Function works.</figcaption>
</figure>
