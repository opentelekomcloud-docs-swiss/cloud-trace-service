:original_name: cts_api_0331_01.html

.. _cts_api_0331_01:

Querying the Tracker Quota of a Tenant
======================================

Function
--------

This API is used to query the tracker quota of a tenant.

URI
---

GET /v3/{project_id}/quotas

.. table:: **Table 1** URI parameter

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                      |
   +============+===========+========+==================================================================================================+
   | project_id | Yes       | String | Project ID. For details, see section :ref:`Obtain the Account ID and Project ID <cts_api_0126>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 2** Response body parameter

   +-----------+----------------------------------------------------------------------------------------------+------------------------------+
   | Parameter | Type                                                                                         | Description                  |
   +===========+==============================================================================================+==============================+
   | resources | Array of :ref:`Quota <cts_api_0331_01__en-us_topic_0000001167759356_response_quota>` objects | List of tracker information. |
   +-----------+----------------------------------------------------------------------------------------------+------------------------------+

.. _cts_api_0331_01__en-us_topic_0000001167759356_response_quota:

.. table:: **Table 3** Quota

   ========= ====== ==========================
   Parameter Type   Description
   ========= ====== ==========================
   type      String Quota resource type.
   used      Long   Number of used resources.
   quota     Long   Total number of resources.
   ========= ====== ==========================

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error description.
   ========== ====== ====================================

Example Request
---------------

.. code-block:: text

   GET https://{endpoint}/v3/{project_id}/quotas

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "resources" : [{
       "type" : "system_tracker",
       "used" : 1,
       "quota" : 1
     } ]
   }

Status Codes
------------

+-------------+-------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                           |
+=============+=======================================================================================================+
| 200         | The request is successful.                                                                            |
+-------------+-------------------------------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                                             |
+-------------+-------------------------------------------------------------------------------------------------------+
| 401         | The request is rejected due to authentication failure.                                                |
+-------------+-------------------------------------------------------------------------------------------------------+
| 403         | The server understood the request but refused to authorize it.                                        |
+-------------+-------------------------------------------------------------------------------------------------------+
| 404         | The requested resource does not exist.                                                                |
+-------------+-------------------------------------------------------------------------------------------------------+
| 500         | Failed to complete the request because of an internal service error.                                  |
+-------------+-------------------------------------------------------------------------------------------------------+
| 503         | The requested service is unavailable. The client should not repeat the request without modifications. |
+-------------+-------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <cts_api_0125>`.
