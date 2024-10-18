:original_name: cts_api_0008.html

.. _cts_api_0008:

Getting Started
===============

This section describes how to create a tracker by calling APIs.

.. note::

   The token obtained from IAM is valid for only 24 hours. If you want to use the same token for authentication, you can cache it to avoid frequent calling of the IAM API.

Involved APIs
-------------

For token-based authentication, you must obtain a token and add **X-Auth-Token** to the request header when calling an API.

-  IAM API used to obtain a token
-  CTS API used to create a tracker

Procedure
---------

#. Obtain a token by referring to :ref:`Authentication <cts_api_0004>`.

#. Send **POST /v1.0/ {project_id} /tracker**.

#. Add **Content-Type** and **X-Auth-Token** to the request header.

#. Set parameters in the request body as follows:

   .. code-block:: text

      POST /v1.0/{project_id}/tracker
      {
       "bucket_name": "obs-f1da",  //Name of an Object Storage Service (OBS) bucket to which traces will be transferred. This parameter is mandatory and its value is a string.
        "is_support_trace_files_encryption": true,  //Whether trace files will be encrypted during transfer. This parameter is optional and its value is of boolean type.
       "is_obs_created": true,  //Whether a new OBS bucket will be created. This parameter is optional and its value is of boolean type.
       "file_prefix_name": "yO8Q",   //File name prefix to mark trace files that need to be stored in OBS. This parameter is optional and its value is a string.
        "log_file_validate": {
       "is_support_validate": true  //Whether trace files will be verified. This parameter is optional and its value is of boolean type.
       }
      }

   If the request is successful, information about the created tracker is returned.

   .. code-block::

      {
       "bucket_name": "obs-f1da",
       "file_prefix_name": "yO8Q",
       "is_obs_created": true,
        "log_file_validate": {
       "is_support_validate": true
       },
      "tracker_name": "system",  //Tracker name
      "status": "enabled"  //Tracker status
      }

   If the request fails, an error code and error message are returned. For details, see :ref:`Error Codes <errorcode>`.
