:original_name: cts_api_0017.html

.. _cts_api_0017:

Deleting a Tracker
==================

Function
--------

This API is used to delete a tracker from CTS. Deleting a tracker has no impact on the operation records that have been generated. When you enable CTS again, you can still view those traces.

URI
---

DELETE /v1.0/{project_id}/tracker

.. table:: **Table 1** Path parameter

   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                 |
   +============+===========+========+=============================================================================================================+
   | project_id | Yes       | String | Project ID. For details about how to obtain a project ID, see :ref:`Obtaining a Project ID <cts_api_0005>`. |
   +------------+-----------+--------+-------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameter

   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                                                                                         |
   +==============+===========+========+=====================================================================================================================================================================================+
   | tracker_name | Yes       | String | Tracker name. If this parameter is not specified, all trackers of a tenant will be deleted. Currently, only one tracker is allowed for each tenant. The tracker name is **system**. |
   +--------------+-----------+--------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

None

Example Request
---------------

.. code-block:: text

   DELETE https://{endpoint}/v1.0/{project_id}/tracker?tracker_name=system

Example Response
----------------

None

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------+
| Status Code | Description                                                                             |
+=============+=========================================================================================+
| 204         | The deletion is successful.                                                             |
+-------------+-----------------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                               |
+-------------+-----------------------------------------------------------------------------------------+
| 401         | The request is rejected due to authentication failure.                                  |
+-------------+-----------------------------------------------------------------------------------------+
| 403         | The server understood the request but refused to authorize it.                          |
+-------------+-----------------------------------------------------------------------------------------+
| 404         | The server failed to find the requested resource or some trackers failed to be deleted. |
+-------------+-----------------------------------------------------------------------------------------+
| 500         | The request failed to be executed or some trackers failed to be deleted.                |
+-------------+-----------------------------------------------------------------------------------------+

Error Codes
-----------

For details, see :ref:`Error Codes <errorcode>`.
