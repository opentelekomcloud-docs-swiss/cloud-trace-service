:original_name: cts_api_0203.html

.. _cts_api_0203:

Querying a Tracker (v3.0)
=========================

Function
--------

After CTS is enabled, you can view details about the tracker on the **Tracker** page. The details include the name of the tracker, name of the OBS bucket for storing traces, and prefix of the trace files stored in the OBS bucket.

URI
---

GET /v3/{project_id}/trackers

.. table:: **Table 1** URI parameter

   +------------+-----------+--------+------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                              |
   +============+===========+========+==========================================================================================+
   | project_id | Yes       | String | Project ID. For details, see :ref:`Obtain the Account ID and Project ID <cts_api_0126>`. |
   +------------+-----------+--------+------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query parameters

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                 |
   +=================+=================+=================+=============================================================================================+
   | tracker_name    | No              | String          | Tracker name. If this parameter is not specified, all trackers of a tenant will be queried. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------+
   | tracker_type    | No              | String          | Tracker type. The value can be **system** (management tracker).                             |
   |                 |                 |                 |                                                                                             |
   |                 |                 |                 | Enumerated value:                                                                           |
   |                 |                 |                 |                                                                                             |
   |                 |                 |                 | -  **system**                                                                               |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------+

Request Parameters
------------------

None

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 3** Response body parameter

   +-----------+-----------------------------------------------------------------------------------------------------------------------+------------------------------+
   | Parameter | Type                                                                                                                  | Description                  |
   +===========+=======================================================================================================================+==============================+
   | trackers  | Array of :ref:`TrackerResponseBody <cts_api_0203__en-us_topic_0000001213357773_response_trackerresponsebody>` objects | List of tracker information. |
   +-----------+-----------------------------------------------------------------------------------------------------------------------+------------------------------+

.. _cts_api_0203__en-us_topic_0000001213357773_response_trackerresponsebody:

.. table:: **Table 4** TrackerResponseBody

   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Type                                                                                    | Description                                                                                                                                                                                    |
   +=======================+=========================================================================================+================================================================================================================================================================================================+
   | id                    | String                                                                                  | Unique tracker ID.                                                                                                                                                                             |
   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | Long                                                                                    | Timestamp when the tracker was created.                                                                                                                                                        |
   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tracker_type          | String                                                                                  | Tracker type. The value can be system (management tracker).                                                                                                                                    |
   |                       |                                                                                         |                                                                                                                                                                                                |
   |                       |                                                                                         | Enumerated value:                                                                                                                                                                              |
   |                       |                                                                                         |                                                                                                                                                                                                |
   |                       |                                                                                         | -  **system**                                                                                                                                                                                  |
   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | domain_id             | String                                                                                  | Account ID. For details, see :ref:`Obtain the Account ID and Project ID <cts_api_0126>`.                                                                                                       |
   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | String                                                                                  | Project ID. For details, see :ref:`Obtain the Account ID and Project ID <cts_api_0126>`.                                                                                                       |
   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | tracker_name          | String                                                                                  | Tracker name. The default value is **system**.                                                                                                                                                 |
   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | status                | String                                                                                  | Tracker status. The value can be **enabled**, **disabled**, or **error**. If the value is set to **error**, the **detail** field is required for specifying the source of the error.           |
   |                       |                                                                                         |                                                                                                                                                                                                |
   |                       |                                                                                         | Enumerated value:                                                                                                                                                                              |
   |                       |                                                                                         |                                                                                                                                                                                                |
   |                       |                                                                                         | -  **enabled**                                                                                                                                                                                 |
   |                       |                                                                                         | -  **disabled**                                                                                                                                                                                |
   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | detail                | String                                                                                  | This parameter is returned only when the tracker status is **error**. It indicates the cause of the abnormal status, and its value can be **bucketPolicyError**, **noBucket**, or **arrears**. |
   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | obs_info              | :ref:`ObsInfo <cts_api_0203__en-us_topic_0000001213357773_response_obsinfo>` object     | Information about the bucket to which traces are transferred.                                                                                                                                  |
   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lts                   | :ref:`lts <cts_api_0203__en-us_topic_0000001213357773_response_databucketquery>` object | Trace Analysis                                                                                                                                                                                 |
   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | group_id              | String                                                                                  | LTS log group ID.                                                                                                                                                                              |
   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | stream_id             | String                                                                                  | LTS log stream ID.                                                                                                                                                                             |
   +-----------------------+-----------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _cts_api_0203__en-us_topic_0000001213357773_response_obsinfo:

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

.. _cts_api_0203__en-us_topic_0000001213357773_response_databucketquery:

.. table:: **Table 6** lts

   +----------------+---------+--------------------------------------------------------------+
   | Parameter      | Type    | Description                                                  |
   +================+=========+==============================================================+
   | is_lts_enabled | Boolean | Specifies whether the LTS search function is enabled.        |
   +----------------+---------+--------------------------------------------------------------+
   | log_group_name | String  | Specifies the name of the log group that CTS creates in LTS. |
   +----------------+---------+--------------------------------------------------------------+
   | log_topic_name | String  | Specifies the name of the log topic that CTS creates in LTS. |
   +----------------+---------+--------------------------------------------------------------+

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

.. code-block:: text

   GET https://{endpoint}/v3/{project_id}/trackers?tracker_name=system

Example Response
----------------

**Status code: 200**

The request is successful.

.. code-block::

   {
     "trackers" : [ {
       "create_time" : 1589886034121,
       "stream_id" : "4a1ef2b6-d79a-4dc6-90f0-48151cd5491b",
       "kms_id" : "7dbbb3fa-93e4-4528-bc7b-9beb794b0229",
       "group_id" : "26fa12ac-75f7-42ed-8118-ab9f2263042f",
       "obs_info" : {
         "is_obs_created" : false,
         "bucket_name" : "",
         "file_prefix_name" : "",
         "bucket_lifecycle" : 0
       },
       "tracker_type" : "system",
       "domain_id" : "2306579dc99f4c8690b14b68e734fcd9",
       "project_id" : "24edf66e79d04187acb99a463e610764",
       "tracker_name" : "system",
       "id" : "ebf8d1c3-762b-4ce3-b316-6b1aa32f8be3",
       "status" : "enabled"
     }
    ]
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
| 500         | Failed to complete the request because of an internal service error.                                  |
+-------------+-------------------------------------------------------------------------------------------------------+
| 503         | The requested service is unavailable. The client should not repeat the request without modifications. |
+-------------+-------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <cts_api_0125>`.
