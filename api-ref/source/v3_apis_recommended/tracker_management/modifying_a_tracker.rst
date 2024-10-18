:original_name: cts_api_0322.html

.. _cts_api_0322:

Modifying a Tracker
===================

Function
--------

This API is used to modify configurations of a tracker, including trace transfer to OBS buckets, key event notifications, trace file encryption, trace search and analysis using LTS, trace file integrity check, and tracker enablement or disablement. Modifying tracker parameters does not affect the existing operation records. After the modification is complete, the new rules are immediately applied to operation recording.

URI
---

PUT /v3/{project_id}/tracker

.. table:: **Table 1** Path parameters

   +------------+-----------+--------+--------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                |
   +============+===========+========+============================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtaining an Account ID and Project ID <cts_api_0005>`. |
   +------------+-----------+--------+--------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                             | Description                                                                                                                                |
   +=================+=================+==================================================================================================+============================================================================================================================================+
   | tracker_type    | Yes             | String                                                                                           | Tracker type. The value can be **system** (management tracker).                                                                            |
   |                 |                 |                                                                                                  |                                                                                                                                            |
   |                 |                 |                                                                                                  | Enumerated values:                                                                                                                         |
   |                 |                 |                                                                                                  |                                                                                                                                            |
   |                 |                 |                                                                                                  | -  **system**                                                                                                                              |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | tracker_name    | Yes             | String                                                                                           | Tracker name. When **tracker_type** is set to **system**, the default value **system** is used.                                            |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | String                                                                                           | Tracker status. The value can be **enabled** or **disabled**. If you change the value to **disabled**, the tracker stops recording traces. |
   |                 |                 |                                                                                                  |                                                                                                                                            |
   |                 |                 |                                                                                                  | Enumerated values:                                                                                                                         |
   |                 |                 |                                                                                                  |                                                                                                                                            |
   |                 |                 |                                                                                                  | -  **enabled**                                                                                                                             |
   |                 |                 |                                                                                                  | -  **disabled**                                                                                                                            |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_info        | No              | :ref:`TrackerObsInfo <cts_api_0322__en-us_topic_0000001213559237_request_trackerobsinfo>` object | Configurations of an OBS bucket to which traces will be transferred.                                                                       |
   +-----------------+-----------------+--------------------------------------------------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------+

.. _cts_api_0322__en-us_topic_0000001213559237_request_trackerobsinfo:

.. table:: **Table 3** TrackerObsInfo

   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter          | Mandatory       | Type            | Description                                                                                                                                                                                      |
   +====================+=================+=================+==================================================================================================================================================================================================+
   | bucket_name        | No              | String          | OBS bucket name. The value contains 3 to 63 characters and must start with a digit or lowercase letter. Only lowercase letters, digits, hyphens (-), and periods (.) are allowed.                |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | file_prefix_name   | No              | String          | Prefix of trace files that need to be stored in OBS buckets. The value can contain 0 to 64 characters, including letters, digits, hyphens (-), underscores (_), and periods (.).                 |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_obs_created     | No              | Boolean         | Whether an OBS bucket is created. If the value is **true**, an OBS bucket will be created to store trace files. If the value is **false**, trace files will be stored in an existing OBS bucket. |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | compress_type      | No              | String          | Compression type. The value can be JSON (no compression) or GZIP (compression). The default format is GZIP.                                                                                      |
   |                    |                 |                 |                                                                                                                                                                                                  |
   |                    |                 |                 | Enumerated values:                                                                                                                                                                               |
   |                    |                 |                 |                                                                                                                                                                                                  |
   |                    |                 |                 | -  **gzip**                                                                                                                                                                                      |
   |                    |                 |                 | -  **json**                                                                                                                                                                                      |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_sort_by_service | No              | Boolean         | Whether to sort the path by cloud service. If this option is enabled, the cloud service name is added to the transfer file path. The default value is **true**.                                  |
   +--------------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 400**

.. table:: **Table 4** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error message.
   ========== ====== ====================================

**Status code: 401**

.. table:: **Table 5** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error message.
   ========== ====== ====================================

**Status code: 403**

.. table:: **Table 6** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error message.
   ========== ====== ====================================

**Status code: 404**

.. table:: **Table 7** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error message.
   ========== ====== ====================================

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error message.
   ========== ====== ====================================

**Status code: 503**

.. table:: **Table 9** Response body parameters

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error message.
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
          "is_obs_created" : false,
          "bucket_name" : "test-data-tracker",
          "file_prefix_name" : "11"
        },
        "is_support_validate" : false,
        "status" : "enabled"
      }

Example Response
----------------

None

Status Codes
------------

+-------------+---------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                       |
+=============+===================================================================================================+
| 200         | The request is successful.                                                                        |
+-------------+---------------------------------------------------------------------------------------------------+
| 400         | The server failed to process the request.                                                         |
+-------------+---------------------------------------------------------------------------------------------------+
| 401         | The request is rejected due to authentication failure.                                            |
+-------------+---------------------------------------------------------------------------------------------------+
| 403         | The server understood the request but refused to authorize it.                                    |
+-------------+---------------------------------------------------------------------------------------------------+
| 404         | The server failed to find the requested resource.                                                 |
+-------------+---------------------------------------------------------------------------------------------------+
| 500         | Failed to complete the request because of an internal service error.                              |
+-------------+---------------------------------------------------------------------------------------------------+
| 503         | The requested service is invalid. The client should not repeat the request without modifications. |
+-------------+---------------------------------------------------------------------------------------------------+

Error Code
----------

For details, see :ref:`Error Codes <errorcode>`.
