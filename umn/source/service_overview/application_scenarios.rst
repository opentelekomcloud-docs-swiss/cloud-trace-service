:original_name: cts_01_0004.html

.. _cts_01_0004:

Application Scenarios
=====================

CTS can be used in the following four scenarios.

Compliance Auditing
-------------------

CTS helps you obtain certifications for auditing in industry standards, such as PCI DSS and ISO 27001, for your service systems.

If you want to migrate your services to the cloud, you will need to ensure the compliance of your own service systems, and the cloud vendor you choose will need to ensure the compliance of your service systems and resources.

CTS plays an important role in compliance. The service records operations of almost all services and resources, and carries out security measures such as encryption, disaster recovery, and anti-tampering to ensure the integrity of traces during their transmission and storage. In addition, you can use CTS to design and implement solutions that help you obtain compliance certifications for your service systems.

Key Event Notifications
-----------------------

CTS works with FunctionGraph to send notifications to natural persons or service APIs when any key operation is performed. The following are real application examples:

-  You can configure HTTP or HTTPS notifications targeted at your independent systems and synchronize traces received by CTS to your own audit systems for auditing.
-  You can select a certain type of log as a trigger (such as file upload) in FunctionGraph to trigger the preset workflow (for example, convert the file format), simplifying service deployment and O&M and avoiding problems and risks.

Data Mining
-----------

CTS mines data in traces to facilitate service health analysis, risk analysis, resource tracking, and cost analysis. You can also obtain the data from CTS and explore the data value yourself.

A trace contains up to fields, recording when an operation was performed by a specific user on a specific resource and the IP address from which the operation was performed.

By configuring HTTP or HTTPS notifications, you can synchronize traces to your own system for analysis. In addition, CTS is connected to Cloud Eye and Log Tank Service (LTS) to help you monitor high-risk operations, detect unauthorized operations, and analyze resource usage.

Fault Locating and Analysis
---------------------------

You can configure filters to pinpoint the faulty operation and its details when a fault occurs, reducing the time and manpower required for detecting, locating, and fixing faults.

CTS provides the following search dimensions: trace type, trace source, resource type, filter, operator and trace status. Each trace contains the request and response of an operation. Querying traces is one of the most efficient methods for locating a fault.

If a problem occurs on the cloud, you can configure filters to search for all suspicious operations in a specified time period. You can then synchronize the relevant traces to O&M and customer service personnel who will handle the problem.
