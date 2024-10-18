:original_name: cts_api_0028.html

.. _cts_api_0028:

Concepts
========

-  User

   An IAM user is created by an account in IAM to use cloud services. Each IAM user has its own identity credentials (password and access keys).

   The account name, username, and password will be required for API authentication.

-  Region

-  AZ

   An AZ comprises one or multiple physical data centers equipped with independent ventilation, fire, water, and electricity facilities. Computing, network, storage, and other resources in an AZ are logically divided into multiple clusters. AZs within a region are interconnected using high-speed optical fibers to allow you to build cross-AZ high-availability systems.

-  Project

   A project corresponds to a region. Projects group and isolate resources (including compute, storage, and network resources) across physical regions. Users can be granted permissions in a default project to access all resources in the region associated with the project. If you need more refined access control, create subprojects under a default project and create resources in subprojects. Then you can assign users the permissions required to access only the resources in the specific subprojects.


   .. figure:: /_static/images/en-us_image_0000001819970050.png
      :alt: **Figure 1** Project isolation model

      **Figure 1** Project isolation model
