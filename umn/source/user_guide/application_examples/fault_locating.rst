:original_name: cts_03_0007.html

.. _cts_03_0007:

Fault Locating
==============

Scenario
--------

If a resource or an action encounters an exception, you can query operation records of the resource or action in a specified time period and view the requests and responses to facilitate fault locating.

Prerequisites
-------------

You have enabled CTS and trackers are running properly.

Procedure
---------

**The following shows how to locate an ECS fault which occurred in a morning.**

#. Log in to the management console as a CTS administrator.
#. Click |image1| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.
#. Choose **Trace List** in the navigation pane on the left.
#. Set filters in sequence and click **Query**.

   .. note::

      Select **Management** for **Trace Type**, **ECS** for **Trace Source**, **ecs** for **Resource Type**, **Resource ID** for **Search By**, and enter the ID of the faulty virtual machine (VM). In the upper right corner, select a time range from 06:00:00 to 12:00:00 on the day when the fault occurred. Then, click **Query** to view the result.

#. Check the returned traces, especially the request type and response of each trace. Pay attention to traces whose status is **warning** or **incident**, and traces whose response indicates a failure.

**The following shows how to locate a fault after an ECS server failed to be created.**

#. Log in to the management console as a CTS administrator.
#. Click |image2| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.
#. Choose **Trace List** in the navigation pane on the left.
#. Select **Management** for **Trace Type**, **ECS** for **Trace Source**, **ecs** for **Resource Type**, and **Warning** for **Trace Status**. In the returned traces, locate the trace named **createServer**.
#. Check the trace details and locate the fault based on the error code or error message.

.. |image1| image:: /_static/images/en-us_image_0000001232870297.png
.. |image2| image:: /_static/images/en-us_image_0000001232950241.png
