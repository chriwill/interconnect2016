# Using Watson Trade-Off Analytics with Node-RED to Analyze Flight Options

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

Because we added a new service to an application it will ask to 'Restage' the application, click on 'RESTAGE'.

<img src="images/Bluemix_Restage_Application.png" width="150">





X.)

[Sample Flight Data](https://raw.githubusercontent.com/chriwill/interconnect2016/master/flightstradeoffanalytics/data/flightdata.json)
