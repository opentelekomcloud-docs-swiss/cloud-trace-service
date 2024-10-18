:original_name: cts_api_0005.html

.. _cts_api_0005:

Obtaining an Account ID and Project ID
======================================

Obtaining Account and Project IDs from the Console
--------------------------------------------------

Account ID (**domain-id**) and project ID are required for some URLs when an API is called. You can perform the following operations to obtain these IDs:

#. Log in to the management console. Hover the mouse pointer over the username and choose **My Credentials** from the drop-down list.
#. On the **My Credentials** page, view the account and project IDs.

If there are multiple projects in one region, expand **Region** and view sub-project IDs from the **Project ID** column.

Obtaining Project IDs by Calling an API
---------------------------------------

The API for obtaining a project ID is **GET https://**\ *{Endpoint}*\ **/v3/projects**. *{Endpoint}* indicates the endpoint of IAM.

In the following example, **id** indicates a project ID.

.. code-block::

   {
       "projects": [
           {
               "domain_id": "65382450e8f64ac0870cd180xxxx",
               "is_domain": false,
               "parent_id": "65382450e8f64ac0870cd180d1xxxx",
               "name": "xx-region-1",
               "description": "",
               "links": {
                   "next": null,
                   "previous": null,
                   "self": "https://www.example.com/v3/projects/a4a5d4098fb4474fa22cd05f89xxxx"
               },
               "id": "a4a5d4098fb4474fa22cd0xxxx",
               "enabled": true
           }
       ],
       "links": {
           "next": null,
           "previous": null,
           "self": "https://www.example.com/v3/projects"
       }
   }
