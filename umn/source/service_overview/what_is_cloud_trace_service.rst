:original_name: en-us_topic_0071185699.html

.. _en-us_topic_0071185699:

What Is Cloud Trace Service
===========================

The log audit module is a core component necessary for information security audit and an important part for the information systems of enterprises and public institutions to provide security risk management and control.

Cloud Trace Service (CTS) is a log audit service for security. It allows you to collect, store, and query resource operation records. You can use these records to perform security analysis, track resource changes, audit compliance, backtrack problems, and locate faults.


.. figure:: /_static/images/en-us_image_0179741594.png
   :alt: **Figure 1** CTS service diagram

   **Figure 1** CTS service diagram

CTS provides the following functions:

-  Trace recording: CTS records operations performed on the management console or by calling APIs, as well as operations triggered by each interconnected service.
-  Trace query: You can query operation records of the last seven days on the CTS console using filters such as trace type, trace source, resource type, filter, operator, and trace status.
-  Trace transfer: Traces can be transferred to Object Storage Service (OBS) buckets or Log Tank Service (LTS) log streams periodically. During transfer, traces are compressed into trace files by service.
-  Trace file encryption: Trace files are encrypted using keys provided by Data Encryption Workshop (DEW) during transfer.
-  Key event notification: CTS works with Simple Message Notification (SMN) to send notifications to your mobile phones and email addresses to notify you of certain key operations.

CTS records:

-  Operations performed on the management console.
-  Operations performed by calling supported APIs.
-  Operations triggered by connected cloud services.
