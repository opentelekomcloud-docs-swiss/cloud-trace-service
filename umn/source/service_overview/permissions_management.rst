:original_name: cts_01_0006.html

.. _cts_01_0006:

Permissions Management
======================

You can use Identity and Access Management (IAM) to manage CTS permissions and control access to your resources. IAM provides identity authentication, permissions management, and access control.

With IAM, you can use your account to create IAM users for your employees, and assign permissions to the users to control their access to resource types. For example, you can create IAM users for software developers and assign specific permissions to allow them to use CTS resources but prevent them from deleting resources or performing any high-risk operations.

If your account does not require individual IAM users for permissions management, skip this section.

IAM can be used free of charge. You pay only for the resources in your account. For details, see `IAM Service Overview <https://docs.sc.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__.

CTS Permissions
---------------

By default, new IAM users do not have any permissions assigned. To assign permissions to these new users, add them to one or more groups, and attach permissions policies or roles to these groups.

CTS is a project-level service deployed and accessed in specific physical regions. When assigning CTS permissions to a user group, specify region-specific projects where the permissions will take effect. If you select **All projects**, the permissions will be granted for all region-specific projects. When accessing CTS, the users need to switch to a region where they have been authorized to use this service.

You can grant users permissions by using roles and policies.

-  Roles: A type of coarse-grained authorization mechanism that provides only a limited number of service-level roles. When using roles to grant permissions, you also need to assign dependency roles. Roles are not an ideal choice for fine-grained authorization and secure access control.
-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization for more secure access control. For example, you can grant ECS users only the permissions for managing a certain type of ECSs. Most policies define permissions based on APIs.

For the API actions supported by CTS, see :ref:`Table 1 <cts_01_0006__en-us_topic_0179741566_table8486434381>`.

.. _cts_01_0006__en-us_topic_0179741566_table8486434381:

.. table:: **Table 1** System-defined roles and policies supported by CTS

   +--------------------+-------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------+
   | Role/Policy Name   | Description                                                                                           | Type                  | Dependency                                                                                                     |
   +====================+=======================================================================================================+=======================+================================================================================================================+
   | CTS FullAccess     | Full permissions for CTS.                                                                             | System-defined policy | None                                                                                                           |
   +--------------------+-------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------+
   | CTS ReadOnlyAccess | Read-only permissions for CTS.                                                                        | System-defined policy | None                                                                                                           |
   +--------------------+-------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------+
   | CTS Administrator  | Administrator permissions for CTS. Users granted these permissions can perform all operations on CTS. | System-defined role   | This role must be used together with the **Tenant Guest** and **OBS Administrator** roles in the same project. |
   |                    |                                                                                                       |                       |                                                                                                                |
   |                    | Users with this permission can perform read-only operations on all services except IAM.               |                       |                                                                                                                |
   +--------------------+-------------------------------------------------------------------------------------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------+

:ref:`Table 2 <cts_01_0006__en-us_topic_0179741566_table4497545191017>` lists the common operations supported by each system-defined policy or role of CTS. Select the policies or roles as required.

.. _cts_01_0006__en-us_topic_0179741566_table4497545191017:

.. table:: **Table 2** Common operations supported by system-defined policies or roles

   +------------------------------------+----------------+--------------------+-------------------+
   | Operation                          | CTS FullAccess | CTS ReadOnlyAccess | CTS Administrator |
   +====================================+================+====================+===================+
   | Querying traces                    | Y              | Y                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Querying quotas                    | Y              | Y                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Creating a tracker                 | Y              | x                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Modifying a tracker                | Y              | x                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Disabling a tracker                | Y              | x                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Enabling a tracker                 | Y              | x                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Querying a tracker                 | Y              | Y                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Deleting a tracker                 | Y              | x                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Creating a key event notification  | Y              | x                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Modifying a key event notification | Y              | x                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Disabling a key event notification | Y              | x                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Enabling a key event notification  | Y              | x                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Querying a key event notification  | Y              | Y                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+
   | Deleting a key event notification  | Y              | x                  | Y                 |
   +------------------------------------+----------------+--------------------+-------------------+

Custom Permissions Policies
---------------------------

You can create custom permissions policies to supplement the system-defined policies.

-  For details, see `Creating a Custom Policy <https://docs.sc.otc.t-systems.com/usermanual/iam/iam_01_0016.html>`__.
