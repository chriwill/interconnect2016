# Using Watson Trade-Off Analytics with Node-RED to Analyze Flight Options - Step-by-Step Guide

Overview
<img src="images/Node_RED_Overview.png" width="450">

1.) Create Node-RED Application on Bluemix

Once you're logged in to your Bluemix account go to 'Catalog' and click on the 'Node-RED Starter Community' application. 

<img src="images/Bluemix_Catalog_Node_RED.png" width="450">

On the right side of the screen you must give it a name, which must be unique. Then click 'Create'. Right now the Node-RED application is being created and deployed.

<img src="images/Bluemix_Catalog_Node_RED_Create.png" width="250">

Staging will take a few minutes.

<img src="images/Bluemix_Staging_Node_RED.png" width="250">

2.) Add Service Watson Tradeoff Analytics

Once Node-RED application staging completed, go back to Catalog and search for 'Tradeoff Analytics' and click on the application icon.

<img src="images/Bluemix_Catalog_Tradeoff_Analytics.png" width="350">

On the next page bind the service to our previously created Node-RED application and click 'Create'.

<img src="images/Bluemix_Catalog_Tradeoff_Create.png" width="250">

Next it will ask to restage the application to use the newly added service, click on 'RESTAGE'.

<img src="images/Bluemix_Restage_Application.png" width="250">

3.) Start using Node-RED application

Once restaging is complete, click on the link to open the Node-RED application.

<img src="images/Node_RED_is_running.png" width="300">

Click on 'Go to your Node-RED flow editor'.

<img src="images/Node_RED_flow_editor.png" width="200">

4.) Create Application Flow





X.) Add Sample Flight Data

[Sample Flight Data](https://raw.githubusercontent.com/chriwill/interconnect2016/master/flightstradeoffanalytics/data/flightdata.json)
