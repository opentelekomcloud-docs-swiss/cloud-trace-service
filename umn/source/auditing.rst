:original_name: cts_03_0021_01.html

.. _cts_03_0021_01:

Auditing
========

Cloud Trace Service (CTS) provides records of operations performed on cloud service resources.

With CTS, you can record operations associated with CTS itself for later query, audit, and backtracking.

.. table:: **Table 1** CTS operations that can be recorded by itself

   +-------------------------------------------------+---------------+--------------------------+
   | Operation                                       | Resource Type | Trace Name               |
   +=================================================+===============+==========================+
   | Creating a tracker                              | tracker       | createTracker            |
   +-------------------------------------------------+---------------+--------------------------+
   | Modifying a tracker                             | tracker       | updateTracker            |
   +-------------------------------------------------+---------------+--------------------------+
   | Disabling a tracker                             | tracker       | updateTracker            |
   +-------------------------------------------------+---------------+--------------------------+
   | Enabling a tracker                              | tracker       | updateTracker            |
   +-------------------------------------------------+---------------+--------------------------+
   | Deleting a tracker                              | tracker       | deleteTracker            |
   +-------------------------------------------------+---------------+--------------------------+
   | Creating a key event notification               | notification  | createNotification       |
   +-------------------------------------------------+---------------+--------------------------+
   | Deleting a key event notification               | notification  | deleteNotification       |
   +-------------------------------------------------+---------------+--------------------------+
   | Modifying a key event notification              | notification  | updateNotification       |
   +-------------------------------------------------+---------------+--------------------------+
   | Changing the status of a key event notification | notification  | updateNotificationStatus |
   +-------------------------------------------------+---------------+--------------------------+
   | Disabling a key event notification              | notification  | updateNotification       |
   +-------------------------------------------------+---------------+--------------------------+
   | Enabling a key event notification               | notification  | updateNotification       |
   +-------------------------------------------------+---------------+--------------------------+
   | Exporting traces                                | trace         | getTrace                 |
   +-------------------------------------------------+---------------+--------------------------+
