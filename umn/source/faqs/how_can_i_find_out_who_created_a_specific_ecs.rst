:original_name: cts_faq_0912.html

.. _cts_faq_0912:

How Can I Find Out Who Created a Specific ECS?
==============================================

Solution
--------

To identify the user who created a specific ECS, you can view traces recorded by CTS.

Prerequisites
-------------

-  You have enabled CTS.
-  You have obtained the resource ID of the ECS.

Procedure
---------

Log in to the CTS console, choose **Trace List**, and select **ECS** for **Trace Source**. In the displayed traces, look for the **createServer** trace with the obtained resource ID, and expand the trace details.

The **user** field shows details of the IAM user who created the ECS. The format is **{"name": "**\ *Account name*\ **", "id": "**\ *Account ID*\ **", "domain"{"name": "**\ *IAM user name*\ **", "id": "**\ *IAM user ID*\ **"}}**. If the ECS was created by an account, the IAM user name and the account name are the same.
