:original_name: en-us_topic_0030594187.html

.. _en-us_topic_0030594187:

What Is Cloud Trace Service
===========================

The log audit module is a core component necessary for information security audit and an important part for the information systems of enterprises and public institutions to provide security risk management and control.

Cloud Trace Service (CTS) is a log audit service for security. It allows you to collect, store, and query resource operation records. You can use these records to perform security analysis, track resource changes, audit compliance, and locate faults.


.. figure:: /_static/images/en-us_image_0179741594.png
   :alt: **Figure 1** CTS service diagram

   **Figure 1** CTS service diagram

CTS provides the following functions:

-  Trace recording: CTS records operations performed on the management console or by calling APIs, as well as operations triggered by each interconnected service.
-  Trace query: Operation records of the last seven days can be queried on the management console from multiple dimensions, such as the trace type, trace source, resource type, filter, operator and trace status.
-  Trace transfer: Traces are transferred to Object Storage Service (OBS) buckets on a regular basis for long-term storage. In this process, traces are compressed into trace files by service.
