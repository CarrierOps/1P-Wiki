# Data Best Practices

## Brief Overview
This file discusses some of the best design practices with regards to using data within a database for the client. It's important to try to and utilize our data in an efficient way to prevent/minimize exponential growth of incurred costs. 

## Design Mindset

Please analyze **Figure 1** and make sure it makes sense. Please reach out if it does not. In terms of building client facing tools, we should aim to be **AGILE**. In terms of constructing queries that power these tools, we should aim to use the **WATERFALL** approach; hence why it's very encouraged to use **CTEs** & **recursive CTEs** when building queries. The **AI solutions**, well they might start off great, they progressively get worse over time...

<figure align="center">
    <img src="../imgs/SOP/data_building.png" width="95%">
  <figcaption>Figure 1: Design Mindset</figcaption>
</figure>


## 3 Coding Principles To Be More Efficent
