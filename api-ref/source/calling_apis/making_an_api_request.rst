:original_name: cts_api_0007.html

.. _cts_api_0007:

Making an API Request
=====================

This section describes the structure of a REST API request, and uses the IAM API for as an example to demonstrate how to call an API. The obtained token can then be used to authenticate the calling of other APIs.

Request URI
-----------

A request URI is in the following format:

**{URI-scheme} :// {Endpoint} / {resource-path} ? {query-string}**

Although a request URI is included in the request header, most programming languages or frameworks require the request URI to be transmitted separately.

-  **URI-scheme**:

   Protocol used to transmit requests. All APIs use **HTTPS**.

-  **Endpoint**:

   Domain name or IP address of the server bearing the REST service. The endpoint varies between services in different regions. It can be obtained from .

-  **resource-path**:

   Access path of an API for performing a specified operation. Obtain the path from the URI of an API. For example, the **resource-path** of the API used to obtain a user token is **/v3/auth/tokens**.

-  **query-string**:

   Query parameter, which is optional. Ensure that a question mark (?) is included before each query parameter that is in the format of "**Parameter name=Parameter value**". For example, **?limit=10** indicates that a maximum of 10 data records will be displayed.

.. note::

   To simplify the URI display, each API is provided only with a **resource-path** and a request method. The **URI-scheme** of all APIs is **HTTPS**, and the endpoints of all APIs in the same region are identical.

Request Methods
---------------

The HTTP protocol defines the following request methods that can be used to send a request to the server:

-  **GET**: requests a server to return specified resources.
-  **PUT**: requests a server to update specified resources.
-  **POST**: requests a server to add resources or perform special operations.
-  **DELETE**: requests a server to delete specified resources, for example, objects.
-  **HEAD**: same as GET except that the server must return only the response header.
-  **PATCH**: requests a server to update a part of a specified resource. If the resource does not exist, a new resource will be created.

For example, in the case of the API used to obtain a user token, the request method is **POST**. The request is as follows:

Request Header
--------------

You can also add additional header fields to a request, such as the fields required by a specified URI or HTTP method. For example, to request for the authentication information, add **Content-Type**, which specifies the request body type.

:ref:`Table 1 <cts_api_0007__en-us_topic_0192137669_table1986821153312>` lists the common request header fields.

.. _cts_api_0007__en-us_topic_0192137669_table1986821153312:

.. table:: **Table 1** Common request header fields

   +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+----------------------------------+
   | Parameter       | Description                                                                                                                                                                                                                                                                                                            | Mandatory                                         | Example Value                    |
   +=================+========================================================================================================================================================================================================================================================================================================================+===================================================+==================================+
   | Host            | Specifies the server domain name and port number of the resources being requested. The value can be obtained from the URL of the service API. The value is in the format of *Hostname*:*Port number*. If the port number is not specified, the default port is used. The default port number for **https** is **443**. | No                                                | code.test.com                    |
   |                 |                                                                                                                                                                                                                                                                                                                        |                                                   |                                  |
   |                 |                                                                                                                                                                                                                                                                                                                        | This field is mandatory for AK/SK authentication. | or                               |
   |                 |                                                                                                                                                                                                                                                                                                                        |                                                   |                                  |
   |                 |                                                                                                                                                                                                                                                                                                                        |                                                   | code.test.com:443                |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+----------------------------------+
   | Content-Type    | Specifies the type (or format) of the message body. The default value **application/json** is recommended. Other values of this field will be provided for specific APIs if any.                                                                                                                                       | Yes                                               | application/json                 |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+----------------------------------+
   | Content-Length  | Specifies the length of the request body. The unit is byte.                                                                                                                                                                                                                                                            | No                                                | 3495                             |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+----------------------------------+
   | X-Project-Id    | Specifies the project ID. Obtain it by referring to :ref:`Obtaining an Account ID and Project ID <cts_api_0005>`.                                                                                                                                                                                                      | No                                                | e9993fc787d94b6c886cbaa340f9c0f4 |
   +-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------------------------------------------------+----------------------------------+

.. note::

   In addition to supporting token-based authentication, APIs also support authentication using access key ID/secret access key (AK/SK). During AK/SK-based authentication, an SDK is used to sign a request, and the **Authorization** (signature information) and **X-Sdk-Date** (time when the request is sent) header fields are automatically added to the request.

   For details, see "AK/SK-based Authentication" in :ref:`Authentication <cts_api_0004>`.

The API used to does not require authentication. Therefore, only the **Content-Type** field needs to be added to requests for calling the API. An example of such requests is as follows:

Request Body (Optional)
-----------------------

This part is optional. A request body transfer information other than the request header and is often sent in a structured format (for example, JSON or XML) defined by the **Content-Type** header field.

A request body varies between APIs. Some APIs do not require the request body, such as the APIs requested using the GET and DELETE methods.

In the case of the API used to , the request parameters and parameter description can be obtained from the API request. The following provides an example request with a body included. Replace **username**, **domainname**, **\*******\*** (login password), and **xxxxxxxxxxxxxxxxx** (project name) with the actual values. Obtain a project name from .

.. note::

   The **scope** parameter specifies where a token takes effect. In the following example, the token takes effect only for the resources in a specified project. For more information about this API, see .

::

   Content-Type: application/json

   {
       "auth": {
           "identity": {
               "methods": [
                   "password"
               ],
               "password": {
                   "user": {
                       "name": "username",
                       "password": "********",
                       "domain": {
                           "name": "domainname"
                       }
                   }
               }
           },
           "scope": {
               "project": {
                   "name": "xxxxxxxxxxxxxxxxxx"
               }
           }
       }
   }

If all data required for the API request is available, you can send the request to call an API through `curl <https://curl.haxx.se/>`__, `Postman <https://www.getpostman.com/>`__, or coding. In the response to the API used to obtain a user token, **x-subject-token** is the desired user token. This token can then be used to authenticate the calling of other APIs.
