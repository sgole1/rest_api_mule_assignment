# rest_api_mule_assignment
Interaction of use case 1 with the API: The consumer flow is designed to fetch the customer details on the basis of customer id(this api can be custamized further to add creation date parameter and get the collection customer objects) using the .raml file /customer api specification. The received input from this api is consumed further by the same flow using the /customer (post) api request. The /customer(post) api then can be enhanced to store the received customer details in to any persistence storage.

Interaction of use case 2 with the API: The given Customer APIs are exchanged and published using the API manager on API portal and made public. Limiting policy can be aplied on get and update flow   

·         Commentary on how the API could be extended for use case 3

·         Commentary on any 'interesting' design decisions you made (and alternative options considered)
