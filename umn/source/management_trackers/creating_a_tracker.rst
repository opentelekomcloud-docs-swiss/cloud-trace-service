:original_name: cts_03_5105.html

.. _cts_03_5105:

Creating a Tracker
==================

If you log in to CTS for the first time, click **Enable CTS** on the **Tracker List** page. A management tracker named **system** will be automatically created. The management tracker identifies and associates with all cloud services your tenant account is using, and records all operations of your tenant account.

Constraints
-----------

-  CTS records operations performed in the last seven days. To store traces for a longer period, configure a tracker to transfer them to OBS or LTS. The tracker will then continuously transfer traces to your specified OBS bucket or LTS log stream for storage.
-  CTS can have only one management tracker. The stored historical traces are retained even after the management tracker is deleted. When you enable CTS again, the management tracker is restored.
