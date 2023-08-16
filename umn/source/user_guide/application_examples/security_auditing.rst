:original_name: cts_03_0006.html

.. _cts_03_0006:

Security Auditing
=================

Scenario
--------

You can query operation records matching specified conditions and check whether operations have been performed by authorized users for security analysis.

Prerequisites
-------------

You have enabled CTS and trackers are running properly.

Procedure
---------

The following takes the records of EVS disk creation and deletion in the last two weeks as an example.

#. Log in to the management console as a CTS administrator.

#. Click |image1| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.

#. Choose **Trace List** in the navigation pane on the left.

#. .. _cts_03_0006__en-us_topic_0170932679_li8526497437:

   Set filters in sequence and click **Query**.

   .. note::

      Select **Management** for **Trace Type**, **EVS** for **Trace Source**, **evs** for **Resource Type**, **Trace name** for **Search By**, select **createVolume** or **deleteVolume**, and click **Query**. By default, all EVS disk creation or deletion operations in the last hour are queried. You can also set the time range to query all EVS creation or deletion operations performed in the last 7 days at most.

#. Choose **Tracker List** in the navigation pane on the left.

#. Download traces older than seven days or all traces by following the instructions in :ref:`Querying Archived Traces <cts_02_0006>`.

#. .. _cts_03_0006__en-us_topic_0170932679_li38255771182015:

   In the trace files, search traces using keywords **createVolume** or **deleteVolume**.

#. Check the traces obtained from steps :ref:`5 <cts_03_0006__en-us_topic_0170932679_li8526497437>` and :ref:`7 <cts_03_0006__en-us_topic_0170932679_li38255771182015>` to see whether there are any unauthorized operations or operations that do not conform to security rules.

.. |image1| image:: /_static/images/en-us_image_0000001187470664.png
