:original_name: cts_api_0201.html

.. _cts_api_0201:

Creating a Tracker (v3.0)
=========================

Function
--------

When you enable CTS, a tracker is automatically created to associate with the cloud services you are using and record all operations on the services. Currently, only one management tracker can be created for a cloud account in a region. Traces are retained in the CTS console for seven days. For long-term storage, you can enable Object Storage Service (OBS) and deliver real-time operation records to OBS buckets.

URI
---

POST /v3/{project_id}/tracker

.. table:: **Table 1** URI parameter

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtain the Account ID and Project ID <cts_api_0126>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request body parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                      |
   +=================+=================+=================+==================================================================================================================================================================================+
   | tracker_type    | Yes             | String          | Tracker type. The value can be system (management tracker).                                                                                                                      |
   |                 |                 |                 |                                                                                                                                                                                  |
   |                 |                 |                 | Enumerated value:                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                  |
   |                 |                 |                 | -  **system**                                                                                                                                                                    |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tracker_name    | Yes             | String          | Tracker name. When **tracker_type** is set to **system**, the default value **system** is used.                                                                                  |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_info        | No              | Object          | Configurations of an OBS bucket to which traces will be transferred. For details, see :ref:`TrackerObsInfo <cts_api_0201__en-us_topic_0000001213477715_request_trackerobsinfo>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_lts_enabled  | No              | Boolean         | Indicates whether to enable trace analysis.                                                                                                                                      |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _cts_api_0201__en-us_topic_0000001213477715_request_trackerobsinfo:

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

**Status code: 201**

.. table:: **Table 4** Response body parameter

   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                                                                                                                                                    |
   +=======================+=======================+================================================================================================================================================================================================+
   | id                    | String                | Unique tracker ID.                                                                                                                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                  | Timestamp when the tracker was created.                                                                                                                                                        |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lts                   | Object                | Trace analysis. For details, see :ref:`lts <cts_api_0201__en-us_topic_0000001213477715_response_databucketquery>`.                                                                             |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tracker_type          | String                | Tracker type. The value can be system (management tracker).                                                                                                                                    |
   |                       |                       |                                                                                                                                                                                                |
   |                       |                       | Enumerated value:                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                |
   |                       |                       | -  **system**                                                                                                                                                                                  |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain_id             | String                | Account ID. For details, see :ref:`Obtain the Account ID and Project ID <cts_api_0126>`.                                                                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                | Project ID. For details, see :ref:`Obtain the Account ID and Project ID <cts_api_0126>`.                                                                                                       |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tracker_name          | String                | Tracker name. The default value is **system**.                                                                                                                                                 |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                | Tracker status. The value can be **enabled**, **disabled**, or **error**. If the value is set to **error**, the **detail** field is required for specifying the source of the error.           |
   |                       |                       |                                                                                                                                                                                                |
   |                       |                       | Enumerated value:                                                                                                                                                                              |
   |                       |                       |                                                                                                                                                                                                |
   |                       |                       | -  **enabled**                                                                                                                                                                                 |
   |                       |                       | -  **disabled**                                                                                                                                                                                |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | detail                | String                | This parameter is returned only when the tracker status is **error**. It indicates the cause of the abnormal status, and its value can be **bucketPolicyError**, **noBucket**, or **arrears**. |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_info              | Object                | Information about the bucket to which traces are transferred. For details, see :ref:`ObsInfo <cts_api_0201__en-us_topic_0000001213477715_response_obsinfo>`.                                   |
   +-----------------------+-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _cts_api_0201__en-us_topic_0000001213477715_response_obsinfo:

.. table:: **Table 5** ObsInfo

   +------------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter        | Type    | Description                                                                                                                                                                       |
   +==================+=========+===================================================================================================================================================================================+
   | bucket_name      | String  | OBS bucket name. The value contains 3 to 63 characters and must start with a digit or lowercase letter. Only lowercase letters, digits, hyphens (-), and periods (.) are allowed. |
   +------------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | file_prefix_name | String  | Prefix of trace files that need to be stored in OBS buckets. The value can contain 0 to 64 characters, including letters, digits, hyphens (-), underscores (_), and periods (.).  |
   +------------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | is_obs_created   | Boolean | Whether the OBS bucket is automatically created by the tracker.                                                                                                                   |
   +------------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | bucket_lifecycle | Integer | Duration that traces are stored in the OBS bucket. When **tracker_type** is set to **system**, the default value is **0**, indicating permanent storage.                          |
   +------------------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _cts_api_0201__en-us_topic_0000001213477715_response_databucketquery:

.. table:: **Table 6** lts

   +-----------------------+-----------------------+--------------------------------------------------------------+
   | Parameter             | Type                  | Description                                                  |
   +=======================+=======================+==============================================================+
   | is_lts_enabled        | Boolean               | Specifies whether the LTS search function is enabled.        |
   +-----------------------+-----------------------+--------------------------------------------------------------+
   | log_group_name        | String                | Specifies the name of the log group that CTS creates in LTS. |
   |                       |                       |                                                              |
   | log_topic_name        | String                | Specifies the name of the log topic that CTS creates in LTS. |
   +-----------------------+-----------------------+--------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 7** Response body parameter

   ========== ====== ====================================
   Parameter  Type   Description
   ========== ====== ====================================
   error_code String Error code. Format: **CTS.**\ *XXX*.
   error_msg  String Error description.
   ========== ====== ====================================

Example Request
---------------

-  Creating a management tracker

   .. code-block:: text

      POST https://{endpoint}/v3/{project_id}/tracker

      {
        "tracker_type" : "system",
        "tracker_name" : "system",
        "obs_info" : {
          "bucket_name" : "test-data-tracker",
          "file_prefix_name" : "11"
        },
        "is_lts_enabled" : true
      }

Example Response
----------------

**Status code: 201**

The request is successful.

.. code-block::

   {
     "id" : "2e6fa9b8-8c6e-456d-b5d3-77be972d220b",
     "create_time" : 1587958482923,
     "domain_id" : "aexxxxxxxx4d4fb4bexxxxxxx791fbf",
     "obs_info" : {
       "bucket_name" : "test-bucket",
       "file_prefix_name" : "11",
       "bucket_lifecycle" : 0,
     },
     "project_id" : "bb1xxxxxxxxe4f498cbxxxxxxxx35634",
     "lts" : {
        "is_lts_enabled" : true,
        "log_group_name" : "CTS",
        "log_topic_name" : "system-trace"
      },
     "tracker_name" : "system",
     "tracker_type" : "system",
     "status" : "enabled"
   }

Status Codes
------------

+-------------+-------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                           |
+=============+=======================================================================================================+
| 201         | The request is successful.                                                                            |
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
