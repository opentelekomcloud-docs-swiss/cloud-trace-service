:original_name: cts_api_0204.html

.. _cts_api_0204:

Deleting a Tracker (v3.0)
=========================

Function
--------

This API is used to delete a tracker from CTS. Deleting a tracker has no impact on the operation records that have been generated. When you enable CTS again, you can still view those traces.

URI
---

DELETE /v3/{project_id}/trackers

.. table:: **Table 1** URI parameter

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                      |
   +============+===========+========+==================================================================================================+
   | project_id | Yes       | String | Project ID. For details, see section :ref:`Obtain the Account ID and Project ID <cts_api_0126>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                 |
   +==============+===========+========+=============================================================================================+
   | tracker_name | No        | String | Tracker name. If this parameter is not specified, all trackers of a tenant will be deleted. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 3** Response body parameter

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error description.
   ========== ====== ====================================

Example Request
---------------

.. code-block:: text

   DELETE https://{endpoint}/v3/{project_id}/trackers?tracker_name=system

Example Response
----------------

None

Status Codes
------------

+-------------+-------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                           |
+=============+=======================================================================================================+
| 204         | The deletion is successful.                                                                           |
+-------------+-------------------------------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                                             |
+-------------+-------------------------------------------------------------------------------------------------------+
| 401         | The request is rejected due to authentication failure.                                                |
+-------------+-------------------------------------------------------------------------------------------------------+
| 403         | The server understood the request but refused to authorize it.                                        |
+-------------+-------------------------------------------------------------------------------------------------------+
| 404         | The server failed to find the requested resource or some trackers failed to be deleted.               |
+-------------+-------------------------------------------------------------------------------------------------------+
| 500         | The request failed to be executed or some trackers failed to be deleted.                              |
+-------------+-------------------------------------------------------------------------------------------------------+
| 503         | The requested service is unavailable. The client should not repeat the request without modifications. |
+-------------+-------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <cts_api_0125>`.
