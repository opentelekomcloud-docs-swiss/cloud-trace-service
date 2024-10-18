:original_name: cts_api_0324.html

.. _cts_api_0324:

Deleting a Tracker
==================

Function
--------

This API is used to delete a tracker. Deleting a tracker has no impact on the operation records that have been generated. When you enable CTS again, you can still view those traces.

URI
---

DELETE /v3/{project_id}/trackers

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                |
   +============+===========+========+============================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining an Account ID and Project ID <cts_api_0005>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+
   | Parameter    | Mandatory | Type   | Description                                                                                                   |
   +==============+===========+========+===============================================================================================================+
   | tracker_name | No        | String | Tracker name. If this parameter is not specified, all trackers of the current tenant account will be deleted. |
   +--------------+-----------+--------+---------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 3** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error message.
   ========== ====== ====================================

**Status code: 401**

.. table:: **Table 4** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error message.
   ========== ====== ====================================

**Status code: 403**

.. table:: **Table 5** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error message.
   ========== ====== ====================================

**Status code: 404**

.. table:: **Table 6** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error message.
   ========== ====== ====================================

**Status code: 500**

.. table:: **Table 7** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error message.
   ========== ====== ====================================

**Status code: 503**

.. table:: **Table 8** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error message.
   ========== ====== ====================================

Example Request
---------------

.. code-block:: text

   DELETE https://{endpoint}/v3/{project_id}/trackers?tracker_name=system

Example Response
----------------

None

Status Code
-----------

+-------------+---------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                       |
+=============+===================================================================================================+
| 204         | The deletion is successful.                                                                       |
+-------------+---------------------------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                                         |
+-------------+---------------------------------------------------------------------------------------------------+
| 401         | The request is rejected due to authentication failure.                                            |
+-------------+---------------------------------------------------------------------------------------------------+
| 403         | The server understood the request but refused to authorize it.                                    |
+-------------+---------------------------------------------------------------------------------------------------+
| 404         | The server failed to find the requested resource or some trackers failed to be deleted.           |
+-------------+---------------------------------------------------------------------------------------------------+
| 500         | The request failed to be executed or some trackers failed to be deleted.                          |
+-------------+---------------------------------------------------------------------------------------------------+
| 503         | The requested service is invalid. The client should not repeat the request without modifications. |
+-------------+---------------------------------------------------------------------------------------------------+

Error Code
----------

For details, see :ref:`Error Codes <errorcode>`.
