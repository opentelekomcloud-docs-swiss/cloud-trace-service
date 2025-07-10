:original_name: cts_02_0003.html

.. _cts_02_0003:

Querying Transferred Traces
===========================

Scenarios
---------

CTS periodically sends trace files to OBS buckets. A trace file is a collection of traces. CTS generates trace files based on services and transfer cycle, and adjusts the number of traces contained in each trace file as needed. CTS can also save audit logs to LTS log streams.

This section describes how to view historical operation records in trace files downloaded from OBS buckets and in LTS log streams.

Prerequisites
-------------

You have configured a tracker in CTS and enabled **Transfer to OBS** or **Transfer to LTS**. For details about how to configure a transfer, see :ref:`Configuring a Tracker <en-us_topic_0071185672>`.

Querying Traces Transferred to OBS
----------------------------------

If you enable **Transfer to OBS** when configuring the tracker, traces will be periodically transferred to a specified OBS bucket as trace files for long-term storage.

#. Log in to the management console.

#. Click |image1| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.

#. Choose **Tracker List** in the navigation pane.

#. Click a bucket in the **OBS Bucket** column.


   .. figure:: /_static/images/en-us_image_0000002344705736.png
      :alt: **Figure 1** Selecting an OBS bucket

      **Figure 1** Selecting an OBS bucket

#. In the OBS bucket, locate the file storage path to view the desired trace, and click **Download** on the right to download the file to the default download path of the browser. If you need to save it to a custom path, click **More** > **Download As** on the right.

   -  The trace file storage path is as follows:

      *OBS bucket name*\ **/CloudTraces/**\ *Region*\ **/**\ *Year*\ **/**\ *Month*\ **/**\ *Day*\ **/**\ *Tracker name*\ **/**\ *Cloud service*

      Example: *User-defined name*\ **/CloudTraces/**\ *Region*\ **/2016/5/19/system/ECS**

   -  The trace file naming format is as follows:

      *Trace file prefix*\ **\_CloudTrace\_**\ *Region*/*Region-project*\ \_\ *Time when the trace file was uploaded to OBS: Year-Month-Day*\ **T**\ *Hour-Minute-Second*\ **Z**\ \_\ *Random characters*\ **.json.gz**

      Example: **FilePrefix_CloudTrace\_\ region-project\ \_2024-12-13T01-29-19Z_47b9d51830deff47.json.gz**

   .. note::

      -  The OBS bucket name and trace file prefix are set by you and other parameters are automatically generated.
      -  File download will incur request fees and traffic fees.
      -  If you disable **Sort by Cloud Service** when configuring a tracker to transfer traces to OBS, the cloud service will not be displayed in the transfer path. Example: *User-defined name*\ **/CloudTraces/**\ *Region*\ **/2016/5/19/system**

   For details about key fields in the CTS trace structure, see :ref:`Trace Structure <cts_03_0010>` and :ref:`Example Traces <cts_03_0011>`.

#. Decompress the downloaded package to obtain a JSON file with the same name as the package, as shown in :ref:`Figure 2 <cts_02_0003__en-us_topic_0000001285318397_fig165592091189>`. Open the JSON file using a text file editor to view traces.

   .. _cts_02_0003__en-us_topic_0000001285318397_fig165592091189:

   .. figure:: /_static/images/en-us_image_0000002344545932.png
      :alt: **Figure 2** JSON file

      **Figure 2** JSON file

.. |image1| image:: /_static/images/en-us_image_0000002378503785.png
