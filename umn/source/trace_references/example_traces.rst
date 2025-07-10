:original_name: cts_03_0011.html

.. _cts_03_0011:

Example Traces
==============

This section provides two example traces and describes their key fields to help you better understand traces. You can read other traces in a similar way as shown below.

For details on the fields in a trace file, see :ref:`Trace Structure <cts_03_0010>`.

-  :ref:`ECS Server Creation <cts_03_0011__en-us_topic_0170932743_section3989813611587>`
-  :ref:`EVS Disk Creation <cts_03_0011__en-us_topic_0170932743_section4774064812032>`

.. _cts_03_0011__en-us_topic_0170932743_section3989813611587:

ECS Server Creation
-------------------

.. code-block::

   {
       "trace_id": "cbdd4480-2e03-11ef-82de-cf140e2a70fb",
       "trace_name": "createServer",
       "resource_type": "ecs",
       "trace_rating": "normal",
       "api_version": "1.0",
       "source_ip": "124.71.93.243",
       "domain_id": "7e0d78c85***d0b9b7cba",
       "trace_type": "ConsoleAction",
       "service_type": "ECS",
       "event_type": "system",
       "project_id": "07066c6fc90025a02f6dc01e105b286e",
       "read_only": false,
       "tracker_name": "system",
       "operation_id": "ListSubscriptions",
       "resource_account_id": "7e0d78c85***d0b9b7cba",
       "time": 1718777931170,
       "resource_name": "ecs-test",
       "user": {
           "access_key_id": "HSTAZVL6WYS0J5MYE2GA",
           "account_id": "7e0d78c85***d0b9b7cba",
           "user_name": "IAMUserA",
           "domain": {
               "name": "IAMDomainB",
               "id": "7e0d78c85***d0b9b7cba"
           },
           "name": "IAMUserA",
           "principal_is_root_user": "true",
           "id": "f36972ced***d619f1214",
           "principal_urn": "iam::7e0d78c85***d0b9b7cba:user:IAMUserA",
           "type": "User",
           "principal_id": "f36972ced***d619f1214"
       },
       "record_time": 1718777931170,
       "request": "{\"server\":{\"adminPass\":\"********\",\"extendparam\":{\"chargingMode\":\"0\",\"regionID\":\"cn-north-4\"},\"count\":1,\"metadata\":{\"op_svc_userid\":\"f36972ced***d619f1214\",\"__support_agent_list\":\"hss,ces\"},\"availability_zone\":\"cn-north-4c\",\"description\":\"\",\"name\":\"ecs-test\",\"imageRef\":\"7d940784-ac0a-425f-b3fa-8478f1a1df70\",\"root_volume\":{\"volumetype\":\"GPSSD\",\"extendparam\":{\"resourceSpecCode\":\"GPSSD\",\"resourceType\":\"3\"},\"size\":40,\"metadata\":null,\"hw:passthrough\":\"false\",\"cluster_type\":null,\"cluster_id\":null,\"iops\":null,\"throughput\":null},\"data_volumes\":[],\"flavorRef\":\"sn3.small.1\",\"personality\":[],\"vpcid\":\"250ad46d-9c89-44ec-a97d-293da771b06b\",\"security_groups\":[{\"id\":\"3bb87748-e387-42e5-ad7a-4331638f1321\"}],\"nics\":[{\"subnet_id\":\"1a02d148-e7f9-4a3c-ba58-18099dfbf752\",\"nictype\":\"\",\"ip_address\":\"\",\"port_id\":null,\"binding:profile\":{\"disable_security_groups\":\"false\"},\"extra_dhcp_opts\":[],\"ipv6_bandwidth\":null,\"ipv6_enable\":false,\"driver_mode\":null,\"allowed_address_pairs\":null,\"efi_enable\":false,\"efi_protocol\":null}],\"publicip\":{\"id\":null,\"eip\":{\"bandwidth\":{\"name\":\"ecs-test-bandwidth\",\"size\":1,\"id\":null,\"sharetype\":\"PER\",\"productid\":\"\",\"chargemode\":\"traffic\"},\"extendparam\":{\"chargingMode\":\"postPaid\"},\"iptype\":\"5_bgp\",\"ipproductid\":\"\"}},\"key_name\":\"KeyPair-ebbe\",\"isAutoRename\":false,\"server_tags\":[],\"batch_create_in_multi_az\":false,\"spod_enable\":false,\"user_data\":\"\"}}",
       "message": "success",
       "response": "{\"job_id\":\"ff8080828fe9028a01902f2542df1b10\",\"job_type\":\"createSingleServer\",\"begin_time\":\"2024-06-19T06:18:09.502Z\",\"end_time\":\"2024-06-19T06:18:51.169Z\",\"status\":\"SUCCESS\",\"error_code\":null,\"fail_reason\":null,\"entities\":{\"server_id\":\"7285ea5d-f15c-4d9c-9e4e-37d37023f2f4\"}}",
       "resource_id": "7285ea5d-f15c-4d9c-9e4e-37d37023f2f4",
       "request_id": "null"
   }

Note the following fields:

-  **time** indicates the timestamp when a trace was generated. In this example, the value is **1718777931170**.
-  **user** indicates the user who performed the operation. In this example, the user is **IAMUserA** (**name** field) under the account **IAMDomainB** (**domain** field).
-  **request** indicates the request to create an ECS. It contains basic information about the ECS, such as its name (**ecs-test-bandwidth**) and VPC ID (**250ad46d-9c89-44ec-a97d-293da771b06b**).
-  **response** indicates the response to the ECS creation request. It contains **status** (**SUCCESS** in this example), **error_code** (**null** in this example), and **fail_reason** (**null** in this example).

.. _cts_03_0011__en-us_topic_0170932743_section4774064812032:

EVS Disk Creation
-----------------

.. code-block::

   {
     "trace_id": "c4ddaa0b-2e05-11ef-bdc6-e1851d8cb7fb",
     "trace_name": "deleteVolume",
     "resource_type": "evs",
     "trace_rating": "normal",
     "api_version": "1.0",
     "source_ip": "124.71.93.243",
     "domain_id": "7e0d78c85***d0b9b7cba",
     "trace_type": "ConsoleAction",
     "service_type": "EVS",
     "event_type": "system",
     "project_id": "07066c6fc90025a02f6dc01e105b286e",
     "read_only": false,
     "resource_id": "bc661a99-3088-4e86-899f-fb4f46c2bb71",
     "tracker_name": "system",
     "resource_account_id": "7e0d78c85***d0b9b7cba",
     "time": 1718778778419,
     "user": {
       "access_key_id": "HSTAA8960GPIROJGW19L",
       "account_id": "7e0d78c85***d0b9b7cba",
       "user_name": "IAMUserA",
       "domain": {
         "name": "IAMDomainB",
         "id": "7e0d78c85***d0b9b7cba"
       },
       "name": "IAMUserA",
       "principal_is_root_user": "true",
       "id": "f36972ced***d619f1214",
       "principal_urn": "iam::7e0d78c85***d0b9b7cba:user:IAMUserA",
       "type": "User",
       "principal_id": "f36972ced***d619f1214"
     },
     "record_time": 1718778778419,
     "request": "",
     "response": "{\"job_id\":\"defe9cf7b5ca4566860edbebb181e17a\",\"job_type\":\"deleteVolume\",\"begin_time\":\"2024-06-19T06:32:53.018Z\",\"end_time\":\"2024-06-19T06:32:58.411Z\",\"status\":\"SUCCESS\",\"error_code\":null,\"fail_reason\":null,\"entities\":{\"volume_type\":\"GPSSD\",\"volume_id\":\"bc661a99-3088-4e86-899f-fb4f46c2bb71\",\"size\":10,\"name\":\"volume-d64d\"}}",
     "resource_name": "volume-d64d",
     "request_id": "defe9cf7b5ca4566860edbebb181e17a"
   }

Note the following fields:

-  **time** indicates the timestamp when a trace was generated. In this example, the value is **1718778778419**.
-  **user** indicates the user who performed the operation. In this example, the user is **IAMUserA** (**name** field) under the account **IAMDomainB** (**domain** field).
-  **request**: optional. It is null in this example.
-  **response** records the returned result of disk deletion.
-  **trace_rating** indicates the trace status. It can replace the **response** field to indicate the operation result. In this example, the value is **normal**, indicating that the operation was successful according to :ref:`Trace Structure <cts_03_0010>`.
