:original_name: cts_faq_0918.html

.. _cts_faq_0918:

What If I Cannot Query Traces?
==============================

Background
----------

Traces cannot be queried on the CTS console.

Procedure
---------

#. Check whether you have configured a proper query time range.

   |image1|

#. Check whether you have configured filters correctly. You can combine one or more filters.

   -  **Trace Name**: Enter a trace name.
   -  **Trace ID**: Enter a trace ID.
   -  **Resource Name**: Enter a resource name. If the cloud resource involved in the trace does not have a resource name or the corresponding API operation does not involve the resource name parameter, leave this field empty.
   -  **Resource ID**: Enter a resource ID. Leave this field empty if the resource has no resource ID or if resource creation failed.
   -  **Trace Source**: Select a cloud service name from the drop-down list.
   -  **Resource Type**: Select a resource type from the drop-down list.
   -  **Operator**: Select one or more operators from the drop-down list.
   -  **Trace Status**: Select **normal**, **warning**, or **incident**.

      -  **normal**: The operation succeeded.
      -  **warning**: The operation failed.
      -  **incident**: The operation caused a fault that is more serious than the operation failure, for example, causing other faults.

#. If you still cannot query traces after the preceding steps, submit a service ticket for technical support.

.. |image1| image:: /_static/images/en-us_image_0000001992735649.png
