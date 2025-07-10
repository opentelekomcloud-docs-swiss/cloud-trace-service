:original_name: cts_faq_0913.html

.. _cts_faq_0913:

How Do I Find Out the Login IP Address of an IAM User?
======================================================

Background
----------

If you want to check if there are security risks in your account by examining the login IP addresses and login time of IAM users, you can view traces recorded by CTS.

Prerequisites
-------------

You have enabled CTS.

Procedure
---------

#. Log in to the CTS console.

#. Select a time range and set the following filters in the search box:

   Select **Trace Source** and **IAM**. Select **Trace Name**, enter **login**, and press **Enter**.

   |image1|

#. In the filter result, click the target trace to view its details. **source_ip** indicates the login IP address, and **record_time** indicates the login time.

   |image2|

.. |image1| image:: /_static/images/en-us_image_0000001992715645.png
.. |image2| image:: /_static/images/en-us_image_0000001992720929.png
