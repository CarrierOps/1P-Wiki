# Getting Started In BigQuery

## Getting To The Starting Screen

Once you get access to project related to your program, in the top search bar of wherever you are currently in the Google Cloud Platform, type BigQuery and click the BigQuery Link that comes up.

<figure align="center">
    <img src="../../../imgs/Hello-BQ/Getting to BigQuery.png" width="100%">
  <figcaption>Getting To BigQuery</figcaption>
</figure>

After clicking the link above, you will be taken to the following page as seen in the image labelled _**BigQuery Starting Page**_. You can call this page the editor or workspace in BigQuery.

<figure align="center">
    <img src="../../../imgs/Hello-BQ/BigQuery Intro Screen.png" width="100%">
  <figcaption>BigQuery Starting Page</figcaption>
</figure>

## Exploring Tables In BigQuery

Once you've navigated to the starting screen,here are some of the following things you can do to get started and learn how to use and navigate BigQuery.



<figure align="center">
    <img src="../../../imgs/Hello-BQ/BigQuery Resources.png" height ="50%">
  <figcaption>Resources Side Bar</figcaption>
</figure>

If you click on the arrow beside programs project name, you can see an expanded view of the resources in the project. You can think of these as folders in a traditional file system, but instead of storing files, we are store tables of data. You can further explore what tables and data is in each folder by clicking on the arrow beside each folder as seen in the ***Exploring Tables In BigQuery*** figure.


<figure align="center">
    <img src="../../../imgs/Hello-BQ/Viewing Tables In BigQuery.png" width="100%">
  <figcaption>Exploring Tables In BigQuery</figcaption>
</figure>


When exploring different tables in BigQuery, the 3 most common things to check are the ***Schema***,***Details***, and the ***Preview***.

<figure align="center">
    <img src="../../../imgs/Hello-BQ/BigQuery Editor Top Bar.png" width="100%">
  <figcaption>Different Sections Of A Table</figcaption>
</figure>

* The schema section shows you all of the columns in the table as well as their data types.
* The details sections give you some general information about the tables such as when it was create, how many rows of data there are, and the amount of store the table uses.
* The preview sections shows you what the table looks like and allows to you see some of the specific values in that table.


## Querying In BigQuery
In the BigQuery editor, you should see a + sign. If you click on this it will open a new table that will be labelled untitled with some number following it.

<figure align="center">
    <img src="../../../imgs/Hello-BQ/Querying In BigQuery.png" width="100%">
  <figcaption>Getting Ready To Write A Query</figcaption>
</figure>

Doing so will lead you to a blank editor that looks like the following. This is where you can start writing your SQL queries.

<figure align="center">
    <img src="../../../imgs/Hello-BQ/Empty Editor BigQuery.png" width="100%">
  <figcaption>Writing A Query In BigQuery</figcaption>
</figure>

Here is a simple sample query I ran using the table `raw_customers` in a previous figure.

<figure align="center">
    <img src="../../../imgs/Hello-BQ/Sample Query With Results.png" width="100%">
  <figcaption>Sample Query With Results</figcaption>
</figure>

After writing your SQL query, click on the blue run button to run that query. After it finishes running, you'll see the results from that query in the query results section at the bottom of the screen.


## Viewing your Query Results In Different Tools

If you want to view your query results in a differt place, tool, or file format, you the options to do so in using the ***Save Results*** and ***Explore Data*** tabs in the query results section.


<figure align="center">
    <img src="../../../imgs/Hello-BQ/Exporting and Viewing Data.png" width="100%">
  <figcaption>Exporting And Viewing Options</figcaption>
</figure>

If you click the save results button, you will get the following popup which will allow you to save your query in whatever file format you given a variety of options. The two most common options to export data are in the `csv` or `google sheets` format.

<figure align="center">
    <img src="../../../imgs/Hello-BQ/Exporting Options In BigQuery.png" width="100%">
  <figcaption>Exporting Options In BigQuery</figcaption>
</figure>


You can also choose to connect your data directly to tools such as google sheets and or looker studio which can be very easy and convenient to get a better look at the data  that you queried.

<figure align="center">
    <img src="../../../imgs/Hello-BQ/Exploring Data Options In BigQuery.png" width="100%">
  <figcaption>Exporting Options In BigQuery</figcaption>
</figure>

