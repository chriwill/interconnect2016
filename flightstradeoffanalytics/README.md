# Using Watson Trade-Off Analytics with Node-RED to Analyze Flight Options - Step-by-Step Guide

In this session you will build a travel advisor application that helps to analyze flight data and pick the best flight option based on individual preferences.

<b>Overview:</b>

<img src="images/Node_RED_Overview.png" align="middle" width="750" title="Overview">

<b>1.) Create Node-RED Application on Bluemix</b>

<img src="images/Bluemix_Catalog_Node_RED.png"  width="450">

Once you're logged in to your Bluemix account go to 'Catalog' and click on the 'Node-RED Starter Community' application. 

On the right side of the screen you must give it a name, which must be unique. Then click 'Create'. Right now the Node-RED application is being created and deployed.

<img src="images/Bluemix_Catalog_Node_RED_Create.png"  width="250">

Staging will take a few minutes.

<img src="images/Bluemix_Staging_Node_RED.png" width="250">

<b>2.) Add Service Watson Tradeoff Analytics</b>

Once Node-RED application staging completed, go back to Catalog and search for 'Tradeoff Analytics' and click on the application icon.

<img src="images/Bluemix_Catalog_Tradeoff_Analytics.png" width="350">

On the next page bind the service to our previously created Node-RED application and click 'Create'.

<img src="images/Bluemix_Catalog_Tradeoff_Create.png" width="250">

Next it will ask to restage the application to use the newly added service, click on 'RESTAGE'.

<img src="images/Bluemix_Restage_Application.png" width="250">

<b>3.) Start using Node-RED application</b>

Once restaging is complete, click on the link to open the Node-RED application.

<img src="images/Node_RED_is_running.png" width="300">

Click on 'Go to your Node-RED flow editor'.

<img src="images/Node_RED_flow_editor.png" width="200">

<b>4.) Trade-Off Analytics Widget flow construction</b>

The flow to achieve this has three streams:

4.1) User-interface serving stream

Create Input - HTTP Request

<img src="images/NR_Create_Input.png" width="400">

<img src="images/NR_Modify_Input1.png" width="250">
<img src="images/NR_Modify_Input2.png" width="250">
<img src="images/NR_Modify_Input3.png" width="250">

4.2) Create Output - HTTP Response

<img src="images/NR_Create_Output.png" width="700">

4.3) Add Function & Template to first row

<img src="images/NR_Add_Function_and_Template.png" width="150">

<img src="images/NR_Add_Function_and_Template2.png" width="500">
<img src="images/NR_Connect_Function_and_Template.png" width="500">

4.4) Define Function to supply the Flight data

'Double Click' on our created function node and update the function name to 'Add Flight Data'.
In addition we have to supply sample flight data, a sample data set can be found here : [Sample Flight Data](https://raw.githubusercontent.com/chriwill/interconnect2016/master/flightstradeoffanalytics/data/flightdata.json).

Copy the data set 'Command-C' and paste it into the function definition 'Command-V'.

<img src="images/NR_Flight_Data_Edit_Function.png" width="400">
<img src="images/NR_Flight_Data_Copy.png" width="400">


4.5) Define Template with Tradeoff Analytics widget

Name Template 'Create Widget'
[Widget HTML](https://raw.githubusercontent.com/chriwill/interconnect2016/master/flightstradeoffanalytics/data/widget.txt)

<img src="images/NR_Create_Widget.png" align="right" width="400">

What the \<script> section does is to:
  - Include the widget's script located at "http://ta-cdn.mybluemix.net/v1/TradeoffAnalytics.js"
  - Start the widget initialization with the `loadTradeoffAnalytics()` call, triggered by `window.onload`.  
  - This invokes the constructor, with parameters to set the dilemmas and events callback URLs, and the id of the placeholder widget's \<div>.
  - The `start()` method is called, which will asynchronously build the widget and pull its dependencies.
  - On the TAReady event notification, we invoke `show(problem)`.  This will cause the widget to call-back on the server's `tofaw/dilemmas` URL with the problem for resolution.
  - Once the data has come back from the dilemmas server, the widget shows the problem and triggers onTAShown(), which is used to resize the widget to fit.


4.6) Edit Processing Row 

<img src="images/NR_Add_Change.png" width="100">
<img src="images/NR_Add_Tradeoff.png" width="100">

<img src="images/NR_After_Tradeoff.png" width="600">

Dilemmas serving stream

This flow on tofaw/dilemmas will make some parameters adjustments through a change node, setting subject, columns and options from the payload, storing the incoming problem for later use, and then calling the tradeoff analytics through its Node-RED service node. On return, another change node will adjust the returned payload parameters's problemand resolution to fit the format expected by the widget and return it as a JSON object.

<img src="images/NR_Edit_Change_Input.png" width="350">
<img src="images/NR_Edit_Change_Output.png" width="350">

4.7) Connect Last Row

<img src="images/NR_Connect_Events_HTTP.png" width="400">

<b>5.) Run Deploy</b>

<img src="images/NR_Deploy.png" width="150">

<b>6.) Run the application</b>

<img src="images/NR_Run_Application.png" width="250">

<img src="images/NR_Run_Application2.png" width="650">


