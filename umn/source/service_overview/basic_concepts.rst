:original_name: en-us_topic_0030598498.html

.. _en-us_topic_0030598498:

Basic Concepts
==============

Trackers
--------

When you enable CTS for the first time, a management tracker named **system** is created automatically.

Th management tracker identifies and associates with all cloud services your tenant account is using, and records all operations of your tenant account.

Traces
------

Traces are operation logs of cloud service resources and are captured and stored by CTS. You can view traces to get to know details of operations performed on specific resources.

Trace List
----------

The trace list displays traces generated in the last seven days. These traces record operations (in the last hour by default) on cloud service resources, including creation, modification, and deletion, but do not record query operations.

-  Management traces: record details about creating, configuring, and deleting cloud service resources in your tenant account.

Trace Files
-----------

A trace file is a collection of traces. CTS generates trace files based on services and transfer cycle and send these files to your specified OBS bucket in real time. In most cases, all traces of a service generated in a transfer cycle are compressed into one trace file. However, if there are a large number of traces, CTS will adjust the number of traces contained in each trace file.

Traces files are in JSON format.
