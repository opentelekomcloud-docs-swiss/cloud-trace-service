:original_name: en-us_cts_01_0001.html

.. _en-us_cts_01_0001:

Creating a Key Event Notification
=================================

You can create key event notifications on CTS so that SMN sends you SMS, email, or HTTP/HTTPS notifications of key events. This function is triggered by CTS, and notifications are sent by SMN. SMN sends key event notifications to subscribers. Before setting notifications, you need to know how to create topics and add subscriptions on the SMN console.

Scenarios
---------

You can use this function for:

-  Real-time detection of high-risk operations (such as VM restart and security configuration changes), cost-sensitive operations (such as creating and deleting expensive resources), and service-sensitive operations (such as network configuration changes).
-  Detection of operations such as login of users with admin-level permissions or operations performed by users who do not have the required permissions.
-  Connection with your own audit system: You can synchronize all audit logs to your audit system in real time to analyze the API calling success rate, unauthorized operations, security, and costs.

Constraints
-----------

-  SMN sends key event notifications to subscribers. Before setting notifications, you need to know how to create topics and add subscriptions on the SMN console.
-  You can create up to 100 key event notifications on CTS:

   -  Specify key operations, users, and topics to customize notifications.
   -  Complete key event notifications can be sent to notification topics.
   -  Typical key event notifications can be sent to specified users and notification topics.

-  If CTS and Cloud Eye use the same message topic, they can receive messages from the same terminal but with different content.
-  You can configure one key event notification for operations initiated by a maximum of 50 users in 10 user groups. For each key event notification, you can add users from different user groups, but cannot select multiple user groups at once.
-  After you disable or delete a key event notification, CTS will not send related notifications to subscribers.


Creating a Key Event Notification
---------------------------------

#. Log in to the management console.

#. Click |image1| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.

#. In the navigation pane on the left, choose **Key Event Notifications**.

   The **Key Event Notifications** page is displayed.

#. Click **Create Key Event Notification**. On the displayed page, specify required parameters.

#. Enter a key event notification name.

   **Notification Name**: Identifies key event notifications. This parameter is mandatory. The name can contain up to 64 characters. Only letters, digits, and underscores (_) are allowed.

#. Configure key operations.

   Select the operations that will trigger notifications. When a selected operation is performed, an SMN notification is sent immediately.

   -  **Operation Type**: Select **All**, **Typical**, or **Custom**.

      -  **Typical**: This option is suitable for enterprise routine auditing. Notifications will be sent when your specified operations occur, such as creating or deleting core resources of Elastic Cloud Server (ECS), Virtual Private Cloud (VPC), Elastic Volume Service (EVS), or DEW, and logging in to IAM.

      -  **All**: This option is suitable if you have connected CTS to your own audit system. When **All** is chosen, you cannot deselect operations because all operations on all cloud services that have connected with CTS will trigger notifications. You are advised to use an SMN topic for which HTTPS is selected.

      -  **Custom**: This option is suitable for enterprises that require detection of high-risk, cost-sensitive, service-sensitive, and unauthorized operations. You can connect CTS to your own audit system for log analysis.

         Customize the operations that will trigger notifications. Up to 1,000 operations of 100 services can be added for each notification. For details, see :ref:`Supported Services and Operations <cts_03_0300>`.

#. Configure users.

   SMN messages will be sent to subscribers when the specified users perform key operations.

   -  If you select **All users**, SMN will notify subscribers of key operations initiated by all users.
   -  If you select **Specified users**, SMN will notify subscribers of key operations initiated by your specified users. You can configure up to 50 users across up to 10 user groups. During each selection, you can choose multiple users within a single group, but not multiple groups at once. To add more groups, click **Add** for each one.

#. Configure an SMN topic.

   -  When **Yes** is selected for **Send Notification**:

      -  **SMN Topic**: You can select an existing topic or click **SMN** to create one on the SMN console.

   -  If you do not want to send notifications, no further action is required.

#. Click **OK**.

Managing Key Event Notifications
--------------------------------

After you create a key event notification, you can view its name, status, template, and SMN topic in the notification list and delete it as required.

#. Log in to the management console.

#. Click |image2| in the upper left corner and choose **Management & Deployment** > **Cloud Trace Service**. The CTS console is displayed.

#. Choose **Key Event Notifications** in the navigation pane on the left. On the displayed page, perform the following operations as required. For details, see :ref:`Table 1 <en-us_cts_01_0001__en-us_topic_0000001240718676_en-us_topic_0179639609_table1679219139498>`.

   .. _en-us_cts_01_0001__en-us_topic_0000001240718676_en-us_topic_0179639609_table1679219139498:

   .. table:: **Table 1** Related operations

      +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                                  | Description                                                                                                                        |
      +============================================+====================================================================================================================================+
      | Viewing a key event notification           | Click a notification name to view the operation list and user list details of the notification.                                    |
      +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Enable/Disable a key event notification    | Click **Enable** or **Disable** in the **Operation** column. CTS can trigger key event notifications only after SMN is configured. |
      +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Modifying a key event notification         | Click **Modify** in the **Operation** column.                                                                                      |
      +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Deleting a key event notification          | Click **Delete** in the **Operation** column.                                                                                      |
      +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Searching for a notification               | In the search box above the list, you can search for notifications by notification name, status, template type, or SMN topic.      |
      +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Refreshing the key event notification list | Click |image5| in the upper right corner.                                                                                          |
      +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+
      | Configuring basic settings                 | Click |image6| in the upper right corner to set table text wrapping, fixed operation column position, and custom columns.          |
      +--------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002378663673.png
.. |image2| image:: /_static/images/en-us_image_0000002344705716.png
.. |image3| image:: /_static/images/en-us_image_0000002378503765.png
.. |image4| image:: /_static/images/en-us_image_0000002378503761.png
.. |image5| image:: /_static/images/en-us_image_0000002378503765.png
.. |image6| image:: /_static/images/en-us_image_0000002378503761.png
