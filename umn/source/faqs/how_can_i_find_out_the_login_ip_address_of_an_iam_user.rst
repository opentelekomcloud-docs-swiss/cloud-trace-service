:original_name: cts_faq_0913.html

.. _cts_faq_0913:

How Can I Find Out the Login IP Address of an IAM User?
=======================================================

Solution
--------

If you want to check if there are security risks in your account by examining the login IP addresses and login time of IAM users, you can view traces recorded by CTS.

Prerequisites
-------------

You have enabled CTS.

Procedure
---------

#. Log in to the CTS console, select **IAM** for **Trace Source**, select a time range, and click **Query**.

   |image1|

#. Click **View Trace** in the **Operation** column of a trace to view its details. **source_ip** indicates the login IP address, and **record_time** indicates the login time.

   |image2|

.. |image1| image:: /_static/images/en-us_image_0000001232722851.png
.. |image2| image:: /_static/images/en-us_image_0000001187244448.png
