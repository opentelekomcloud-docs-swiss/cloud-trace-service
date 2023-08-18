:original_name: cts_api_0202.html

.. _cts_api_0202:

Modifying a Tracker (v3.0)
==========================

Function
--------

This API is used to modify configurations of a tracker, including trace transfer to OBS buckets, key event notifications, and trace file encryption. Modifying tracker parameters does not affect the collected traces. After the modification is complete, the new rules are immediately applied to operation recording.

URI
---

PUT /v3/{project_id}/tracker

.. table:: **Table 1** URI parameter

   +------------+-----------+--------+--------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                      |
   +============+===========+========+==================================================================================================+
   | project_id | Yes       | String | Project ID. For details, see section :ref:`Obtain the Account ID and Project ID <cts_api_0126>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                |
   +=================+=================+=================+============================================================================================================================================+
   | tracker_type    | Yes             | String          | Tracker type. The value can be system (management tracker).                                                                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | tracker_name    | Yes             | String          | Tracker name. When **tracker_type** is set to **system**, the default value **system** is used.                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String          | Tracker status. The value can be **enabled** or **disabled**. If you change the value to **disabled**, the tracker stops recording traces. |
   |                 |                 |                 |                                                                                                                                            |
   |                 |                 |                 | Enumerated value:                                                                                                                          |
   |                 |                 |                 |                                                                                                                                            |
   |                 |                 |                 | -  **enabled**                                                                                                                             |
   |                 |                 |                 | -  **disabled**                                                                                                                            |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_info        | No              | object          | Configurations of an OBS bucket to which traces will be transferred.                                                                       |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | is_lts_enabled  | No              | Boolean         | Indicates whether to enable trace analysis.                                                                                                |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 3** TrackerObsInfo

   +------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Mandatory | Type    | Description                                                                                                                                                                       |
   +==================+===========+=========+===================================================================================================================================================================================+
   | bucket_name      | No        | String  | OBS bucket name. The value contains 3 to 63 characters and must start with a digit or lowercase letter. Only lowercase letters, digits, hyphens (-), and periods (.) are allowed. |
   +------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | file_prefix_name | No        | String  | Prefix of trace files that need to be stored in OBS buckets. The value can contain 0 to 64 characters, including letters, digits, hyphens (-), underscores (_), and periods (.).  |
   +------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_obs_created   | No        | Boolean | Whether the OBS bucket is automatically created by the tracker.                                                                                                                   |
   +------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 4** Response body parameter

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error description.
   ========== ====== ====================================

Example Request
---------------

-  Modifying a management tracker

   .. code-block:: text

      PUT https://{endpoint}/v3/{project_id}/tracker

      {
        "tracker_type" : "system",
        "tracker_name" : "system",
        "obs_info" : {
          "bucket_name" : "test-data-tracker",
          "file_prefix_name" : "11"
        },
        "is_lts_enabled" : false,
        "status" : "enabled"
      }

Example Response
----------------

None

Status Code
-----------

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
| 404         | The server failed to find the requested resource.                                                     |
+-------------+-------------------------------------------------------------------------------------------------------+
| 500         | Failed to complete the request because of an internal service error.                                  |
+-------------+-------------------------------------------------------------------------------------------------------+
| 503         | The requested service is unavailable. The client should not repeat the request without modifications. |
+-------------+-------------------------------------------------------------------------------------------------------+

Error Code
----------

See :ref:`Error Codes <cts_api_0125>`.
