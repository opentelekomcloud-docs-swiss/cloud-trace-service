:original_name: cts_02_0003.html

.. _cts_02_0003:

Querying Archived Traces
========================

Scenarios
---------

CTS periodically sends trace files to OBS buckets. A trace file is a collection of traces. CTS generates trace files based on services and transfer cycle, and adjusts the number of traces contained in each trace file as needed.

This section describes how to obtain historical operation records from trace files downloaded from the OBS bucket.

Prerequisites
-------------

You have configured a tracker. For details, see :ref:`Configuring a Tracker <cts_03_0002>`.

Procedure
---------

#. Log in to the management console.

#. Click |image1| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.

#. Choose **Tracker List** in the navigation pane on the left.

#. Click a bucket in the **OBS Bucket** column.

#. In the OBS bucket, select the trace to be viewed based on the trace file storage path, and download the file to the default download path of the browser. If you need to save the event file to a custom path, click **Download As** on the right.

   -  The trace file storage path is as follows:

      **OBS bucket name > CloudTraces > Region > Year > Month > Day > Tracker name > Service directory**

      An example is **User-defined name > CloudTraces > region > 2016 > 5 > 19 > system > ECS**.

   -  The trace file naming format is as follows:

      **Trace file prefix_CloudTrace_Region/Region-project_Time when the trace file was uploaded to OBS: Year-Month-DayTHour-Minute-SecondZ_Random characters.json.gz**

      An example is **File Prefix**\ **\_CloudTrace_region-project_2016-05-30T16-20-56Z_21d36ced8c8af71e.json.gz**.

   .. note::

      The OBS bucket name and trace file prefix are user-defined, and other parameters are automatically generated.

   For details about key fields in the CTS trace structure, see :ref:`Trace Structure <cts_03_0010>` and :ref:`Example Traces <cts_03_0011>`.

#. Decompress the downloaded package to obtain a JSON file with the same name as the package. Open the JSON file using a text file editor to view traces.

.. |image1| image:: /_static/images/en-us_image_0000001232728979.png
