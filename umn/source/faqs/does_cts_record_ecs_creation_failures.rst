:original_name: cts_faq_0927.html

.. _cts_faq_0927:

Does CTS Record ECS Creation Failures?
======================================

Yes. When you create an ECS, the operation and its result will be reported to CTS.

How It Works
------------

With CTS, you can record ECS operations for later query, auditing, and backtracking.

For details about the key ECS operations that can be recorded by CTS, see section "Key Operations Supported by CTS". When you add, delete, or modify an ECS, the ECS service automatically records your operations and results and then sends traces in the specified format to CTS for archiving. CTS stores traces of the last seven days and displays them on the **Trace List** page.

Procedure
---------

#. Log in to the CTS console.

#. On the **Trace List** page, set the time range to **Last 1 week**.

#. In the search box, select **Trace Source** and **ECS**, select **Resource Type** and **ecs**, and then select **Trace Name** and enter **createServer**. Press **Enter** to view the filtering result.

   |image1|

   .. note::

      To obtain traces of the last seven days, use **createServer** as the keyword to query transferred traces in OBS buckets.

.. |image1| image:: /_static/images/en-us_image_0000001992951413.png
