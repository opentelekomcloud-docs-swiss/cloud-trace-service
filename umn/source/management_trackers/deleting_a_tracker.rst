:original_name: cts_03_5108.html

.. _cts_03_5108:

Deleting a Tracker
==================

Scenarios
---------

You can delete the management tracker on the CTS console. Deleting it does not affect the existing operation records. This section describes how to delete the management tracker on the console.

Constraints
-----------

After a tracker is deleted, traces can still be reported to CTS. You can view traces of the last seven days in the trace list. However, new traces recorded after you disable the tracker cannot be viewed and transferred to OBS or LTS, and key event notifications will not be sent.

Enable CTS again to restore the management tracker.

Prerequisites
-------------

You have enabled CTS.

Deleting a Management Tracker
-----------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner to select the desired region and project.
#. Click |image2| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.
#. Choose **Tracker List** in the navigation pane.
#. Click **Delete** in the **Operation** column of the management tracker.
#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000001639826968.png
.. |image2| image:: /_static/images/en-us_image_0000001639667708.png
