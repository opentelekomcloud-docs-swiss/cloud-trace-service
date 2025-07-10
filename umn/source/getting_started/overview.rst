:original_name: cts_02_0001.html

.. _cts_02_0001:

Overview
========

Scenarios
---------

You need to enable CTS before using it. A management tracker named **system** is automatically created when CTS is enabled. All traces recorded by CTS are associated with the tracker.

You can only query operation records of the last seven days on the CTS console. To query operation records generated in the past seven days, store trace files in an OBS bucket or Log Tank Service (LTS) log stream. Ensure that you have enabled OBS and LTS and have full permissions for the OBS bucket and LTS log stream you are going to use. By default, only the owner of OBS buckets can access the buckets and all objects contained in the buckets, but the owner can grant access permissions to other services and users by configuring access policies.

Prerequisites
-------------

-  To configure the trace transfer function, you must enable OBS and LTS.
-  To enable the key event notification function, you must enable Simple Message Notification (SMN).

Associated Services
-------------------

-  OBS: used to store trace files.
-  Data Encryption Workshop (DEW): Provides keys that can be used to encrypt trace files.
-  LTS: stores logs.
-  SMN: Sends email or SMS message notifications to users when key operations are performed.

Enabling CTS for the First Time
-------------------------------

#. Log in to the management console.
#. Click |image1| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.
#. Choose **Tracker List** in the navigation pane on the left and click **Enable CTS** in the upper right corner. A management tracker named **system** will be automatically created.

   .. note::

      The management tracker logs user operations like creation, login, and deletion on all cloud service resources. For details about the cloud services supported by CTS, see :ref:`Supported Services and Operations <cts_03_0300>`.

#. Choose **Tracker List** in the navigation pane to view operation records of the last seven days.

.. |image1| image:: /_static/images/en-us_image_0000002344545948.png
