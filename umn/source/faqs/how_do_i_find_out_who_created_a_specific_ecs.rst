:original_name: cts_faq_0912.html

.. _cts_faq_0912:

How Do I Find Out Who Created a Specific ECS?
=============================================

Background
----------

To identify the user who created a specific ECS, you can view traces recorded by CTS.

Prerequisites
-------------

-  You have enabled CTS.
-  You have obtained the resource ID of the ECS.

Procedure
---------

#. Log in to the CTS console.

#. Choose **Trace List** in the navigation pane.

#. Set the time range to 06:00 to 12:00 of a certain day and set the following filters:

   In the search box, select **Trace Source** and **ECS**. Select **Trace Name**, enter **createServer**, and press **Enter**. Then, select **Resource ID**, enter *{Resource ID of the ECS}*, and press **Enter**.

   |image1|

#. In the filter result, click the target trace to view its details.

   The **user** field shows details of the IAM user who created the ECS. The format is **{"name": "**\ *Account name*\ **", "id": "**\ *Account ID*\ **", "domain"{"name": "**\ *IAM user name*\ **", "id": "**\ *IAM user ID*\ **"}}**. If the ECS was created by an account, the IAM user name and the account name are the same.

.. |image1| image:: /_static/images/en-us_image_0000001992707325.png
