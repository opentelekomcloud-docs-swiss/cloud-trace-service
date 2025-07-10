:original_name: en-us_topic_0030598498.html

.. _en-us_topic_0030598498:

Basic Concepts
==============

Trackers
--------

When you enable CTS for the first time, a management tracker named **system** is created automatically.

The management tracker identifies and associates with all cloud services your tenant account is using, and records all operations of your tenant account.

A management tracker and 100 data trackers can be created for a tenant account.

Currently, only one tracker can be created for each tenant.

Traces
------

Traces are operation logs of cloud service resources and are captured and stored by CTS. You can view traces to get to know details of operations performed on specific resources.

Traces: management traces reported by cloud services.

Trace List
----------

The trace list displays traces generated in the last seven days. These traces record operations (in the last hour by default) on cloud service resources, including creation, modification, and deletion, but do not record query operations.

-  Management traces record details about creating, modifying, and deleting cloud service resources in your tenant account.

Trace Files
-----------

A trace file is a collection of traces. CTS generates trace files based on services and transfer cycle and send these files to your specified OBS bucket in real time. In most cases, all traces of a service generated in a transfer cycle are compressed into one trace file. However, if there are a large number of traces, CTS will adjust the number of traces contained in each trace file.

Traces files are in JSON format. The following is an example of a trace file.


.. figure:: /_static/images/en-us_image_0000002378663633.png
   :alt: **Figure 1** Trace file example

   **Figure 1** Trace file example

Verifying Trace File Integrity
------------------------------

The authenticity of operation records during a security incident investigation is often affected by trace files being deleted or tampered with. The records therefore cannot be used as an effective basis for investigation. Therefore, CTS provides trace file integrity verification to help you ensure the authenticity of trace files.

The verification function for trace file integrity adopts industry standard algorithms and generates a Hash value for each trace file. This Hash value changes when the trace file is modified or deleted. Therefore, by tracking the Hash value, you can confirm whether the trace file is modified. In addition, the RSA algorithm is used to sign on the digest file to ensure that the file is not modified. In this way, any operations of modifying or deleting trace files are recorded by CTS.

After the verification function for trace file integrity is enabled, CTS generates a digest file for Hash values of all trace files recorded in the past hour and synchronizes the digest file to an OBS bucket configured for the current tracker.

CTS signs on each digest file using public and private keys. You can verify the digest file using the public key after the file is stored to the OBS bucket.
