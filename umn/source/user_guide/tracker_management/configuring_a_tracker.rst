:original_name: cts_03_0002.html

.. _cts_03_0002:

Configuring a Tracker
=====================

Scenario
--------

Traces recorded in CTS can be transferred to OBS for long-term storage.

The configuration will take effect immediately after it is complete.

Prerequisites
-------------

You have enabled CTS.

Procedure
---------

#. Log in to the management console.
#. Click |image1| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.
#. Choose **Tracker List** in the navigation pane on the left.
#. On the right of the tracker information, click **Configure**.
#. Click **OK** to complete the configuration.

   .. note::

      Traces recorded by CTS are delivered periodically to the OBS bucket for storage. If you configure an OBS bucket for a tracker, traces generated during the current cycle (usually several minutes) will be delivered to the configured OBS bucket. For example, if the current cycle is from 12:00:00 to 12:05:00 and you configure an OBS bucket for a tracker at 12:02:00, traces received from 12:00:00 to 12:02:00 will also be delivered to the configured OBS bucket for storage at 12:05:00.

.. |image1| image:: /_static/images/en-us_image_0000001187949118.png
