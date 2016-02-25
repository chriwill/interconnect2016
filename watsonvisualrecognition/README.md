# Using Watson Visual Recognition with Node-RED to recognize the content of the image - Step-by-Step Guide

In this lab we will build a travel advisor application that recognizes the content of the image which can be used to provide more information about the destination. 


<h4>Overview :</h4>
<img src="images/Overview.png" height="200" width ="1000" align="center">

<h4>Step 1 : Sign up / Login to Bluemix - https://console.ng.bluemix.net/</h4>



<h4>Step 2 : Go to Catalog tab and search for Node-RED service.</h4>

Click on Node-RED to create the application.

<img src="images/node-red-catalog.png" height="270" width ="500" align="center">



<h4>Step 3 : Click on Node-Red and give a unique name for the application</h4>

<img src="images/create-app.png" height="500" width ="900" align="center">


Staging will take few minutes 

<img src="images/app-staging.png" height="250" width ="450" align="center">


Yayyyy its running and ready to use!!

<img src="images/app-running.png" height="100" width ="350" align="center">


You can verify now that a Node-RED application is created with a Cloudant database

<img src="images/nodered-appstatus.png" height="500" width ="250" align="center">




<h4>Step 4 : Switch to Catalog tab and search for 'Visual Recognition' service</h4>

<img src="images/visularecognition-catalog.png" height="270" width ="500" align="center">





<h4>Step 5 : Create a Visual Recognition service and bind it with Node-RED application created in the above step.</h4>

Select the Node-RED application from the dropdown -

<img src="images/create-visualrecognition-service.png" height="500" width ="950" align="center">
	
	
	
To bind the Visual Recognition service to the Node-RED application, click 'Restage' to restart the node-red application.

<img src="images/restage-request.png" height="200" width ="450" align="center">



Your Visual recognition service is now bound to the Node-RED application

<img src="images/app-overview.png" height="350" width ="700" align="center">



Click on Application url and Navigate to node red flow editor

<img src="images/node-red-editor.png" height="100" width ="300" align="center">	




<h4>Step 6 : Create the application flow in Node-RED editor</h4>

6.1) - Drag and drop the Http node from Input section on the left and also get the http response node form output section.

<img src="images/appflow-step1.png" height="250" width ="700" align="center">	



6.2)  - Double click on the http input node to configure the get API as shown below and click 'Ok'

<img src="images/appflow-step2.png" height="270" width ="500" align="center">	



6.3)  - Double click on http response node and provide name for the node.

<img src="images/appflow-step3.png" height="270" width ="500" align="center">	

	
Click the 'Deploy' button on the top right section of the editor to deploy the application

<img src="images/app-flowstep-deploy.png" height="50" width ="150" align="center">


6.4)  - Search the 'switch' node and add to the flow editor

<img src="images/appflow-step4.png" height="270" width ="800" align="center">	


Configure the switch node that check if no url has been provided then reload the same page (switch nodes are mostly used for if-else cases)

<img src="images/appflow-step5.png" height="500" width ="550" align="center">



6.5)  - Search for 'change' node and add to the flow editor 

<img src="images/appflow-step6.png" height="270" width ="800" align="center">	


Configure it to parse and pass imageurl from the payload object

<img src="images/appflow-step7.png" height="500" width ="550" align="center">	



6.6)  - Search for 'template' node and add 2 template nodes to the editor - 1- Building homepage and 2- Generate report

<img src="images/appflow-step8.png" height="270" width ="1000" align="center">


Configure one of the template node which Creates Application Homepage - 

Change the Syntax Highlight to  - HTML from the dropdown on the left
Copy the raw html content from this same data to the template section [Sample HTML Form Content](https://raw.githubusercontent.com/zankhanapathak/watson-visual-recognition-app/master/application_forms/application_homepage.html).

<img src="images/appflow-step9.png" height="550" width ="650" align="center">


<img src="images/appflow-step10.png" height="270" width ="400" align="center">



Connect the Nodes as shown below : 

To explain the flow- the Get call will pass the imageurl info as payload to the Image parameter node, which then will parse the input and check if its null will reload the same home page and send as response. And If any input is provided it will send the payload to extract the image url node to process it further.

<img src="images/appflow-step11.png" height="200" width ="900" align="center">


Click the 'Deploy' button on the top right section of the editor to deploy the application

<img src="images/app-flowstep-deploy.png" height="50" width ="150" align="center">


6.7)  -  Search for 'Visual Recognition' node and add it to the flow editor and connect it to the Extract Image URL node as shown below

<img src="images/appflow-step12.png" height="500" align="center">



6.8)  -  Configure the remaining 'template' node to generate reports - This template node get the result from the 'Visual recognition' node and sends the ouput to the 'HTTP Response' node

Copy the raw html content from this same data to the template section [Sample HTML Form Content](https://raw.githubusercontent.com/zankhanapathak/watson-visual-recognition-app/master/application_forms/report_form.html).

<img src="images/appflow-step13.png" height="550" width ="500" align="center">


Connect the Visual Recognition, Generate Report and HTTP Response nodes as shown below :

<img src="images/appflow-step14.png" height="270" width ="700" align="center">


Click the 'Deploy' button on the top right section of the editor to deploy the application

<img src="images/app-flowstep-deploy.png" height="50" width ="150" align="center">


Your application is ready to use!!! 

<h4>Step 7 :  Run the Application - Go to your browser and change the URL from the Node-RED application '/red' to '/imagerecognition'.</h4>

<img src="images/appflow-step15.png" height="50" width ="500" align="center">


<img src="images/Application-homepage.png" width="850">


<b>Appendix) Application flow file</b>

You can download the complete flow file [here](https://raw.githubusercontent.com/zankhanapathak/watson-visual-recognition-app/master/application_forms/visualapp_node_red_export.json)  and import it into your Node-RED instance.

<img src="images/NR_Import1.png" align="top" height="250" width="300">
<img src="images/NR_Import2.png" align="top" height="250" width="400">

