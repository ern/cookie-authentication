Cookie Authentication
=====================

This example shows how Mule can act as a proxy to a Web application which exposes resources in Xml and Json format. Access to the resources is controlled by way of 
cookies which can store the id of the session (session.id in this example). When a GET is sent to a resource with no cookie in the header, the server responds with
a 302 redirect and Location of the page to redirect to (the login page in this example).
The flow follows this redirect (not automatically so as to retrieve the value of Set-Cookie. This value is stored on the in-memory Object Store and subsequent requests
will reuse this cookie value and thus avoid the login page while the session lasts.
A successful login will result in a 302 redirect response from the server with the Location being the url of the originally requested resource.

ObjectStore
===========
Mule can exploit the ObjectStore to store state (by default Mule is stateless). The ObjectStore is in-memory by default (though it is necessary to specify a partition value, otherwise
it will be persistent by default. Partition values allows for segregration of storage for multi-tenancy scenarios). 

Contact
=======

nial.darbey@mulesoft.com