# mulesoft-product-system-api

 

+ [Use Case](#usecase)
+ [Considerations](#considerations)
	* [APIs security considerations](#apissecurityconsiderations)
+ [Run it!](#runit)
	* [Running on Studio](#runonstudio)
	* [Running on CloudHub](#runoncloudhub)
	* [Note](#RequiredDetailstorunonlocalandcloudhub)
	


# Use Case <a name="usecase"/>

mulesoft-product-system-api is system api being called by mulesoft-shoppingcart-process-api to get the product details when add/update/delete operations are triggered.This api allows us to look up product inventory and allow user to add/update/delete product in shopping cart based on availabilty.This is a dummy api which fetches the product details for given product id against the product catalog master file stored within api itself.

### GET/weworkinventory and attributes.queryParams.productId
This endpoint will trigger subflow implementation-logic which retrives the specific product object from product-master-catalog.json based on productId passed as query parameter.Example metadata-
   {
   "b71aaec3-7da1-4f3b-9dc1-47cfa54e2420": {
      "Product": "Dedicated Desk 1",
      "Location": "Minneapolis",
      "Subscription Method": "Monthly",
      "Unit": "Month",
      "Amount": "$500/month"
   }
   }

 

# Considerations <a name="considerations"/>

To run this api in local enviroment, there are certain preconditions that must be considered. **Failling to do so could lead to unexpected behavior of the api.**

## APIs security considerations <a name="apissecurityconsiderations"/>
This system API is  deployed to CloudHub and managed using the API Platform Manager.
   

# Run it! <a name="runit"/>
Simple steps to get mulesoft-product-system-api running.
See below.


### Where to Download Mule Studio and Mule ESB
Here are few tips to download Anypoint Studio.

+ You can download Mule Studio from this [Location](https://www.mulesoft.com/lp/dl/studio)


### Importing an mulesoft-product-system-api into Studio
Anypoint Studio offers several ways to import a project into the workspace, for example: 

+ Anypoint Studio Project from File System
+ Packaged mule application (.jar)


### Running on Studio <a name="runonstudio"/>
Once you have imported  mulesoft-product-system-api into Anypoint Studio you need to follow these steps to run it:

+ Locate the properties file `mulesoft-product-system-api-<env>.yaml`, in src/main/mule/resources as we need to decrypt any credetials using masterKey
+ Once that is done, right click on your Anypoint mulesoft-product-system-api project folder 
+ Hover you mouse over `"Run as"`
+ Click on  `"Mule Application(configure)"`.
+ Click on Enviromet tab.
+ click on Add.
+ Set new environment variable as "Name" : env and "Value" : sandbox
+ Set new environment variable as "Name" : masterKey and "Value" : *********************************


## Running on CloudHub <a name="runoncloudhub"/>
After deploying it to cloudhub, You need to go to `"Manage Application"` > `"Properties"` to set all environment variables detailed in **Properties to be configured**.

anypoint.platform.client_id=*********************************
anypoint.platform.base_url=https://anypoint.mulesoft.com/
anypoint.platform.analytics_base_url=https://analytics-ingest.anypoint.mulesoft.com
masterKey=*********************************
anypoint.platform.client_secret=*********************************
anypoint.platform.config.analytics.agent.enabled=false
env=sandbox

## Note <a name="RequiredDetailstorunonlocalandcloudhub"/>
Please refer Rajnish_ShoppingCart_project.pdf for details on masterKey as well as other credetails required to run in local as well as on cloudhub
 
