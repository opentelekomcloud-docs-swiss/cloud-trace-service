:original_name: cts_03_0006.html

.. _cts_03_0006:

Security Auditing
=================

Scenarios
---------

You can query operation records matching specified conditions and check whether operations have been performed by authorized users for security analysis.

This section describes how to use CTS to audit EVS creation and deletion operations performed in the last two weeks.

Constraints
-----------

To store operation records for longer than seven days, you must configure transfer to OBS or LTS for trackers so that you can view them in OBS buckets or LTS log groups.

Prerequisites
-------------

You have enabled CTS and trackers are running properly.

Viewing Real-Time Traces
------------------------

The following takes the records of EVS disk creation and deletion in the last two weeks as an example.

#. Log in to the management console as a CTS administrator.

#. Click |image1| in the upper left corner to select the desired region and project.

#. Click |image2| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.

#. Choose **Trace List** in the left navigation pane.

#. .. _cts_03_0006__en-us_topic_0170932679_li8526497437:

   Set the time range to **Last 1 week**, set filters in sequence, and click **Query**.

   .. note::

      Select **Management** for **Trace Type**, **evs** for **Trace Source**, **evs** for **Resource Type**, **Trace name** for **Search By**, select **createVolume** or **deleteVolume**, and click **Query**. By default, all EVS disk creation or deletion operations performed in the last hour are queried. You can also set the time range to query all EVS creation or deletion operations performed in the last seven days at most.

#. To query operation records of the last seven days, go to the OBS bucket or LTS log group. For details, see :ref:`Querying Transferred Traces <cts_02_0006>`.

#. Download traces older than seven days or all traces by following the instructions in :ref:`Querying Transferred Traces <cts_02_0006>`.

#. .. _cts_03_0006__en-us_topic_0170932679_li38255771182015:

   In the trace files, search traces using keywords **createVolume** or **deleteVolume**.

#. Check the traces obtained in steps :ref:`5 <cts_03_0006__en-us_topic_0170932679_li8526497437>` and :ref:`8 <cts_03_0006__en-us_topic_0170932679_li38255771182015>` to see whether there are any unauthorized operations or operations that do not conform to security rules.

.. |image1| image:: /_static/images/en-us_image_0000002378503741.png
.. |image2| image:: /_static/images/en-us_image_0000002378663649.png
