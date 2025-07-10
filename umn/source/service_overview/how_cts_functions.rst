:original_name: cts_01_0003.html

.. _cts_01_0003:

How CTS Functions
=================

CTS connects to other cloud services, records operations on cloud resources and the results, and stores these records in the form of trace files to OBS buckets in real time.

You can use CTS to create trackers to record trace files. If trace transfer has been configured, trace files will be stored in the OBS bucket that you have specified.

You can perform the following operations on a trace file:

-  Trace file creation and storage

   -  When you add, delete, or modify resources on services interconnected with CTS, such as Elastic Cloud Server (ECS), Elastic Volume Service (EVS), and Image Management Service (IMS), the target services will record the operations and their results automatically and deliver them in the form of trace files to CTS for archiving.
   -  Operation records of the last seven days are displayed on the CTS console. If trace transfer has been enabled, operation records are periodically delivered to the OBS bucket that you have specified for long-term storage.

-  Trace file query

   -  You can query operation records in the last seven days on the **Trace List** page by time and other filters.
   -  To query operation records earlier than seven days, you can download the trace files stored in OBS buckets if trace transfer has been configured.
   -  You can enable, disable, configure, or delete a tracker on the **Tracker List** page.

   For example, if you create an image using IMS, the service will report the creation operation to CTS. Then, CTS will deliver the trace to an OBS bucket for storage if trace transfer has been configured. You can view trace files in the trace list.
