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
tag  [OBSOLETE]
It returns feeds, in a form of sesnor.xsd conformed, containing data streams tagged with the search query. 
http://APIDOTCOM/v1/feeds?tag=greenhouse

province or null
It returns all the feeds, in a form of sesnor.xsd conformed, within the province.
http://APIDOTCOM/feed.php/anhui
http://APIDOTCOM/feed.php


fd or feed
It returns all sensor information pertaining to the given feed ID. It returns in a form of feed.xsd conformed.
http://APIDOTCOM/sensor.php/23456


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

Deployment:
SQL table shall be created based on the information provided by the sql file, under ./src/sql. This is MySQL compatible.

Two PHP files shall be deployed at the desirable location of Apache web server to serve request. These two files serve 
feed and sensor RESTFul requests.

Please NOTE - The correct MySQL account and password must be replaced to be able to successfully access to the database.
The change is required at the beginning of feed.php and sensor.php.

$link = mysql_connect('localhost', 'acct', 'pass')

Reference:
1. Extended Environment Markup Language - www.eeml.org

版本0.01 – GET operation definition

0.01版 - 创建GET操作定义

这个API是完全基于HTTP的请求协议，符合Representational State Transfer（REST）的设计原则。

RESTful　API的访问使用HTTP的动词，以确定哪些行动对特定的数据对象：

        GET：获取对象的当前状态
        PUT：设置对象的当前状态
        POST：创建一个新的对象
        DELETE删除：删除对象

对于数据检索，如平台的整合，唯一所需的API是GET，虽然会支持PUT以添加标签／tag，提高搜索能力。

参数/说明/示例

feed 或 网关
它返回一串feeds，符合list.xsd的形式，在全省范围内。
http://APIDOTCOM/feed.php/anhui
http://APIDOTCOM/feed.php

sensor
它返回在一个网关（feed）ID之内的所有传感器相关的信息。符合feed.xsd的形式。
http://APIDOTCOM/sensor.php/23456


数据对象：
环境温度表示“amtemp”。
湿度被表示为“humidity”。
土壤温度被表示为“soiltemp”。
土壤湿度表示“soilhumid”。
表示为“sun”。

一个feed 或网关最多支持250传感器。它可以覆盖一个1.5公里半径的地区。传感器和传感器之间最大距离应该可以达到300到500米。最理想的传播视线（line of sight）的是500米。因此，在正常的无线电干扰条件下如温室和混凝土建筑，300米的距离是可以支持。

HTTP状态码

API尝试图返回相应的HTTP状态码（见http://en.wikipedia.org/wiki/List_of_HTTP_status_codes）。

常见的状态代码包括：

        200 OK：成功处理的请求。
        401未授权：要么你需要提供身份验证凭据，或提供的凭证是无效的。
        403禁止访问：服务器能理解你的要求，但拒绝履行它。一位随行的错误消息应该给予解释。
        404未找到：要么你请求一个无效的URI或资源不存在问题（如没有这种饲料）。
        422无法处理的实体：服务器无法创建一个源，因为EEML / JSON是不完整的/有效的（例如，它并没有包括“title”element）。
        500内部服务器错误：发生了错误。
        503无服务器错误：通常发生时，有太多的要求，进入服务器 - 如果你得到这个从一个API请求，那么错误信息会被返回的XML响应。

部署：
/src/sql目录下的sql文件 提供有关的信息，可用于应建立SQL的表格（table）。数据库必须是MySQL兼容的。

两个PHP文件必须被部署在Apache Web服务器的理想的位置（directory）以用于回应HTTP Restful的服务请求。这两个文件是
feed.php和sensor.php 以满足的RESTful请求。

请注意 - 正确的MySQL帐号和密码（'acct', 'pass'）必须被更换，以能够成功地访问数据库。
要更改的地方在开始的feed.php和sensor.php。

$link = mysql_connect('localhost', 'acct', 'pass')
　
参考：
1。扩展环境标记语言 - www.eeml.org


