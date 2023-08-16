:original_name: cts_03_0008.html

.. _cts_03_0008:

Resource Tracking
=================

Scenario
--------

You can view operation records of a cloud resource throughout its lifecycle.

Prerequisites
-------------

You have enabled CTS and trackers are running properly.

Procedure
---------

The following takes the records of all operations on an ECS server as an example.

#. Log in to the management console as a CTS administrator.

#. Click |image1| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.

#. Choose **Trace List** in the navigation pane on the left.

#. .. _cts_03_0008__en-us_topic_0170932730_li36410601182:

   Set filters in sequence and click **Query**.

   .. note::

      Select **Management** for **Trace Type**, **ECS** for **Trace Source**, **ecs** for **Resource Type**, **Resource ID** for **Search By**, enter the ID of the faulty VM, and click **Query**. By default, the matching traces generated in the last hour are returned. You can also set the time range to view the matching traces in the last 7 days at most.

#. Choose **Tracker List** in the navigation pane on the left.

#. .. _cts_03_0008__en-us_topic_0170932730_li14173783182013:

   Download traces older than seven days or all traces by following the instructions in :ref:`Querying Archived Traces <cts_02_0006>`.

#. Check all the traces obtained in :ref:`4 <cts_03_0008__en-us_topic_0170932730_li36410601182>` and :ref:`6 <cts_03_0008__en-us_topic_0170932730_li14173783182013>`.

.. |image1| image:: /_static/images/en-us_image_0000001187630634.png
