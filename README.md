21api
=====

sensor feed API

version 0.01 - creation for GET operation definition

The API is currently entirely based on HTTP requests, and conforms to the design principles of Representational State Transfer (REST). 

RESTful access uses the HTTP verbs to determine which action to make on a particular data object:

        GET : Retrieves the current state of the object
        PUT : Sets the current state of the object
        POST : Creates a new object
        DELETE : Deletes the object

For the data retrieval, such as the platform integration, the only desired API is GET, although PUT will be supported to add tags to enhance search capability.

Parameter/Description/Example
tag
It returns feeds, in a form of sesnor.xsd conformed, containing data streams tagged with the search query. 
http://APIDOTCOM/v1/feeds?tag=greenhouse

province
It returns all the feeds, in a form of sesnor.xsd conformed, within the province.
http://APIDOTCOM/v1/feeds?province=anhui&tag=greenhouse

fd or feed
It returns all sensor information pertaining to the given feed ID. It returns in a form of feed.xsd conformed.
http://APIDOTCOM/v1/feeds?fd=4efbg56sq2


Data objects:
Ambient temperature is denoted as "amtemp".
Humidity is denoted as "humidity".
Soil temperature is denoted as "soiltemp".
Soil humidity is denoted as "soilhumid".
Sun light is denoted as "sun".

One feed or communication adapter has up to 250 sensors to be supported. It can cover an area of 1.5KM radius. The sensor between the sensor or router should be around 300 to 500 meters maximum distance. The line of sight is 500 meters. So give or take in the normal radio interference condition like greenhouse and concrete building, 300 meter can be supported.

HTTP Status Codes

The API attempts to return appropriate HTTP status codes (see http://en.wikipedia.org/wiki/List_of_HTTP_status_codes) for every request.

Common status codes include:

        200 OK: request processed successfully.
        401 Not Authorized: either you need to provide authentication credentials, or the credentials provided aren't valid.
        403 Forbidden: the server understands your request, but refuses to fulfill it. An accompanying error message should explain why.
        404 Not Found: either you're requesting an invalid URI or the resource in question doesn't exist (eg. no such feed).
        422 Unprocessable Entity: the server was unable to create a feed because the EEML/JSON was not complete/valid (e.g. it didn't include a "title" element).
        500 Internal Server Error: Something went wrong.
        503 No server error: usually occurs when there are too many requests coming into the server - if you get this from an API request then the error message will be returned in XML in the response.


Reference:
1. Extended Environment Markup Language - www.eeml.org


