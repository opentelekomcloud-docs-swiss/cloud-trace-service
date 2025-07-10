:original_name: cts_03_0136.html

.. _cts_03_0136:

Permissions Management
======================

You can use Identity and Access Management (IAM) for fine-grained permissions control for your CTS. With IAM, you can:

-  Create IAM users for personnel based on your enterprise's organizational structure. Each IAM user has their own identity credentials for accessing CTS resources.
-  Grant only the permissions required for users to perform a specific task.
-  Entrust other accounts or cloud services to perform efficient O&M on your CTS resources.

If your account does not require individual IAM users, you can skip this section.

Prerequisites
-------------

Before granting permissions to user groups, learn about system-defined permissions in :ref:`Permissions <cts_01_0006>`).

Process Flow
------------


.. figure:: /_static/images/en-us_image_0000002378663637.png
   :alt: **Figure 1** Process of granting CTS permissions

   **Figure 1** Process of granting CTS permissions

#. .. _cts_03_0136__en-us_topic_0207902851_li10961848173315:

   On the IAM console, create a user group and grant it permissions.

   Create a user group on the IAM console, and attach the **CTS Administrator** policy to the group.

#. Create an IAM user and add it to the created user group.

   Create a user on the IAM console and add it to the user group created in :ref:`1 <cts_03_0136__en-us_topic_0207902851_li10961848173315>`.

#. Log in as the IAM user and verify permissions.

   Log in to the console as the user you created, and verify that the user has the assigned permissions.
