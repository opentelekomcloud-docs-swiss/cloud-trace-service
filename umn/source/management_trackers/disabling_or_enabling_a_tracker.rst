:original_name: cts_03_5107.html

.. _cts_03_5107:

Disabling or Enabling a Tracker
===============================

Scenarios
---------

You can enable or disable a tracker on the CTS console. Disabling a tracker does not affect existing operation records.

This section describes how to enable or disable a tracker.

Constraints
-----------

After a tracker is disabled, traces can still be reported to CTS. You can view traces of the last seven days in the trace list. However, new traces recorded after you disable the tracker cannot be viewed and transferred to OBS or LTS, and key event notifications will not be sent.

Prerequisites
-------------

You have enabled CTS.

Disabling or Enabling the Management Tracker
--------------------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner to select the desired region and project.
#. Click |image2| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.
#. Choose **Tracker List** in the navigation pane.
#. Click **Disable** in the **Operation** column in the row of the management tracker.
#. Click **OK**. After the tracker is disabled, the **Disable** button changes to **Enable**.
#. To enable the management tracker again, click **Enable** and then click **OK**. The tracker will start recording operations again.

.. |image1| image:: /_static/images/en-us_image_0000001687987677.png
.. |image2| image:: /_static/images/en-us_image_0000001688106889.png
