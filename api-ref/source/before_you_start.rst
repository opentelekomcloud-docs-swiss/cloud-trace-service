:original_name: cts_api_0001.html

.. _cts_api_0001:

Before You Start
================

Cloud Trace Service (CTS) is a log audit service designed to strengthen cloud security. It allows you to collect, store, and query resource operation records. You can use these records to perform security analysis, track resource changes, audit compliance, and locate faults.

You can use APIs introduced in this document to perform operations on CTS, such as creating and deleting a tracker. For details about all supported operations, see :ref:`API Overview <cts_api_0002>`.

Before calling CTS APIs, ensure that you are familiar with CTS concepts and functions. For details, see *CTS Service Overview*.

Endpoints
---------

An endpoint is the **request address** for calling an API. Endpoints vary depending on services and regions. To obtain the regions and endpoints, contact the enterprise administrator.

Constraints
-----------

-  A maximum of one management tracker can be created in an account. The quotas cannot be modified.
-  For more constraints, see API description.

Concepts
--------

-  Trackers

   Before using CTS, you need to enable it. A tracker is automatically created when CTS is enabled. The tracker identifies and associates with all cloud services you are using, and records all operations on the services.

   A management tracker can be created for a tenant.

-  Traces

   Traces are cloud resource operation logs captured and stored by CTS. You can view traces to identify when operations were performed by which users for tracking.

   Management traces are operation records reported by cloud services.

-  Domain

   An account is created upon successful registration with the cloud system. The account has full access permissions for all of its cloud services and resources. It can be used to reset user passwords and grant user permissions. The account is a payment entity and should not be used directly to perform routine management. For security purposes, create Identity and Access Management (IAM) users and grant them permissions for routine management.

-  User

   An IAM user is created using an account to use cloud services. Each IAM user has their own identity credentials (password and access keys).

   The account name, username, and password will be required for API authentication.

-  Region

-  AZ

   An AZ comprises one or multiple physical data centers equipped with independent ventilation, fire, water, and electricity facilities. Computing, network, storage, and other resources in an AZ are logically divided into multiple clusters. AZs within a region are interconnected using high-speed optical fibers to allow you to build cross-AZ high-availability systems.

-  Project

   A project corresponds to a region. Projects group and isolate resources (including compute, storage, and network resources) across physical regions. Users can be granted permissions in a default project to access all resources in the region associated with the project. If you need more refined access control, create subprojects under a default project and create resources in subprojects. Then you can assign users the permissions required to access only the resources in the specific subprojects.


   .. figure:: /_static/images/en-us_image_0000002255078693.png
      :alt: **Figure 1** Project isolation model

      **Figure 1** Project isolation model

API Versions
------------

It is recommended that you use the V3 APIs, which are more powerful and easy to use.

The V1 APIs will be brought offline soon.
