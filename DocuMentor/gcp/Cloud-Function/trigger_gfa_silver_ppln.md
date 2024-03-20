# trigger_gfa_silver_ppln

## Summary

This function triggers the `gfa_data_silver` in mage. This cloud function is event driven; it runs every time a new file is placed into the `gfa_data` bucket in Google Cloud Storage. This function contains logic to fire of the mage pipeline only if it's replaced in the `raw` subfolder bucket. 

It's trigger the mage pipeline via a post request and passes these runtime variables -> get from mage pipeline


Link pipeline


## dev ops 


## Diagram

<figure align="center">
    <img src="../../../imgs/gcp trigger gfa data.png" width="100%">
  <figcaption>High-level diagram showing the how trigger_gfa_silver_ppln Cloud Function works.</figcaption>
</figure>


