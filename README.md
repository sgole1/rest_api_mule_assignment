# rest_api_mule_assignmen
The code repository contains Customer APIs to perform CRUDs operations. The APIs are designed using the inventorysystem.raml. The .raml is used to create the Mule flows to define APIs flow. A consumer_flow is created for usecase 1 polling once in 5 minutes. Customer get API is used to GET the customer data on the basis of its id and a custome POST api is used to save the data.

Assumptions:
1. Security is not implemented.
2. Assignement is focusing on the APIs standard designs.

-------------------------------------------------------------------
Interaction of use case 1 with the API: 
-------------------------------------------------------------------
The consumer flow is designed to fetch the customer details on the basis of customer id(this api can be custamized further to add creation date parameter and get the collection customer objects) using the .raml file /customer api specification. The received input from this api is consumed further by the same flow using the /customer (post) api request. The /customer(post) api then can be enhanced to store the received customer details in to any persistence storage.

----------------------------------------------------------------------------------------------------------------------------------
Interaction of use case 2 with the API: 
----------------------------------------------
The Http protocol support and usage of application/json allows the various Customer APIs to be integrated with Mobile aplication easily.
The given Customer APIs are proxied, and can be exchanged and published using the API manager on API portal on cloudHub and made public. On cloudhub deployment, limiting policy can be applied on get and update /customer api to limit the number of requests per minute/second. In this way the APIs can used efficiently over the network. 

----------------------------------------------------------------------------------------------------------------------------------
API could be extended for use case 3: 
----------------------------------------

The (inventorysystem.raml)RAML file is defined for Product and Order api as
/product: 
  description: extension for product API
/order: 
  description: extension for order API
These apis would be extended in future further by defining various attributes in (inventorysystem.raml)RAML file.

-----------------------------------------------------------------------------------
The'interesting' design decisions you made (and alternative options considered) : 
----------------------------------------------------------------------------------
1. The input and output object was defined in the (inventorysystem.raml) RAML file using the resourceType attribute. While defining the resource type as Cutomer, additional validation was also enforced to mark all the attributes of customer object as required. As a result this constraint was enforcedon all the Customer APIs. 
2. I have used the concept of versioning in the APIs urls as <https://mocksvc.mulesoft.com/mocks/fb6223c3-5154-4ebd-8bd8-876016db408d/api/1.0/customer> . As a result different versions can be supported for the same api and refered seperately. 
----------------------------------------------------------------------------------------------------------------------------------
RESTful API in Mulesoft with test stubs for the consumer and provider systems.
The APIs url with test stubs are accessible using the below urls 
Get : https://mocksvc.mulesoft.com/mocks/fb6223c3-5154-4ebd-8bd8-876016db408d/api/1.0/customer
Query Parameter : id=1
Content Type : application/json

Get : https://mocksvc.mulesoft.com/mocks/fb6223c3-5154-4ebd-8bd8-876016db408d/api/1.0/customers
Content Type : application/json


