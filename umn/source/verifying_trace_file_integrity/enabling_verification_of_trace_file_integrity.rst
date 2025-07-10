:original_name: cts_03_0013.html

.. _cts_03_0013:

Enabling Verification of Trace File Integrity
=============================================

Scenarios
---------

During a security investigation, operational records will not be able to serve as effective and authentic evidence if they are deleted or tampered with. You can enable the integrity verification on CTS to ensure the authenticity of trace files. CTS supports integrity verification of trace files for trackers configured with OBS transfer.


Enabling Verification of Trace File Integrity
---------------------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner to select the desired region and project.
#. Click |image2| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.
#. Choose **Tracker List** in the navigation pane.

   .. note::

      Click **Enable CTS** if you have not enabled CTS.

#. Click **Configure** in the row of the management tracker **system**. On the displayed **Configure Tracker** page, click **Next**, and enable **Verify Trace File** in the **Configure Transfer** step.

.. |image1| image:: /_static/images/en-us_image_0000001073759763.png
.. |image2| image:: /_static/images/en-us_image_0000001233228729.png
