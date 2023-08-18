:original_name: cts_api_0126.html

.. _cts_api_0126:

Obtain the Account ID and Project ID
====================================

Scenarios
---------

You can manage your security credentials on the My Credentials page.

Obtaining the Project ID by Calling an API
------------------------------------------

The API used to obtain a project ID is GET https://{Endpoint}/v3/projects. {Endpoint} is the IAM endpoint and can be obtained from `Regions and Endpoints <https://docs.sc.otc.t-systems.com/endpoint/index.html>`__.

The following is an example response. The value of **id** is the project ID.

.. code-block::

   {
        "projects": [
            {
                "domain_id": "65382450e8f64ac0870cd180d14e684b",
                "is_domain": false,
                "parent_id": "65382450e8f64ac0870cd180d14e684b",
                "name": "project_name",
                "description": "",
                "links": {
                    "next": null,
                    "previous": null,
                    "self": "https://www.example.com/v3/projects/a4a5d4098fb4474fa22cd05f897d6b99"
                },
                "id": "a4a5d4098fb4474fa22cd05f897d6b99",
                "enabled": true
             }
        ],
        "links": {
            "next": null,
            "previous": null,
            "self": "https://www.example.com/v3/projects"
        }
    }

Obtain a Project ID from the Console
------------------------------------

#. Register yourself on the management console and log in to it.

#. Move your pointer over the username and select My Credential in the displayed drop-down list.

   On the My Credential page, view the project ID in the project list.


   .. figure:: /_static/images/en-us_image_0000001680255017.png
      :alt: **Figure 1** Viewing project IDs

      **Figure 1** Viewing project IDs

Obtaining an Account ID
-----------------------

An account ID is required for some URLs when an API is called. To obtain an account ID, perform the following operations:

#. Log in to the management console.

#. Click the username in the upper right corner and select My Credentials from the drop-down list.

   On the My Credentials page, view Account ID.


   .. figure:: /_static/images/en-us_image_0000001631655364.png
      :alt: **Figure 2** Viewing account IDs

      **Figure 2** Viewing account IDs
