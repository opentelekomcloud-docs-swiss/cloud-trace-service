:original_name: cts_03_0008.html

.. _cts_03_0008:

Resource Tracking
=================

Scenarios
---------

You can view operation records of a cloud resource throughout its lifecycle.

This section describes how to use CTS to view all operation records of an ECS.

Constraints
-----------

To store operation records for longer than seven days, you must configure transfer to OBS or LTS for trackers so that you can view them in OBS buckets or LTS log groups.

Prerequisites
-------------

You have enabled CTS and trackers are running properly.

Viewing Real-Time Traces
------------------------

#. Log in to the management console as a CTS administrator.

#. Click |image1| in the upper left corner to select the desired region and project.

#. Click |image2| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.

#. Choose **Trace List** in the left navigation pane.

#. .. _cts_03_0008__en-us_topic_0170932730_li36410601182:

   Set filters in sequence and click **Query**.

   .. note::

      Select **Management** for **Trace Type**, **ECS** for **Trace Source**, **ecs** for **Resource Type**, **Resource ID** for **Search By**, enter the ID of the VM, and click **Query**. By default, the matching traces generated in the last hour are returned. You can also set the time range to view the matching traces in the last seven days at most.

#. Choose **Tracker List** in the navigation pane. On the displayed page, obtain the OBS bucket or LTS log group information.

#. .. _cts_03_0008__en-us_topic_0170932730_li14173783182013:

   Query traces older than seven days or all traces by following the instructions in :ref:`Querying Transferred Traces <cts_02_0006>`.

#. Check all the traces obtained in :ref:`5 <cts_03_0008__en-us_topic_0170932730_li36410601182>` and :ref:`7 <cts_03_0008__en-us_topic_0170932730_li14173783182013>`.

.. |image1| image:: /_static/images/en-us_image_0000002344545896.png
.. |image2| image:: /_static/images/en-us_image_0000002344545920.png
