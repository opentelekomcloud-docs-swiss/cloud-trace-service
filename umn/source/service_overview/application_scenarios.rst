:original_name: cts_01_0004.html

.. _cts_01_0004:

Application Scenarios
=====================

CTS provides operation records on cloud service resources. A record contains the user who performed the operation, IP address, operation content, and returned response message. With these records, you can better conduct auditing, plan and use resources, and identify operations of high risks or that violate regulations.

CTS can be used in the following scenarios.

-  **Compliance auditing**

   CTS helps you obtain certifications for auditing in industry standards, such as PCI DSS and ISO 27001, for your service systems. CTS allows you to query all operation records of security control. This is essential for enterprises and organizations, especially financial and payment enterprises, to achieve certification.

   If you want to migrate your services to the cloud, you will need to ensure the compliance of your own service systems, and the cloud vendor you choose will need to ensure the compliance of your service systems and resources.

   CTS plays an important role in compliance. The service records operations of almost all services and resources, and carries out security measures such as encryption, disaster recovery, and anti-tampering to ensure the integrity of traces during their transmission and storage. In addition, you can use CTS to design and implement solutions that help you obtain compliance certifications for your service systems.

-  **Key event notifications**

   CTS works with FunctionGraph to send notifications to recipients, including natural persons or service APIs, upon the execution of key operations. The following are real application examples:

   You can configure HTTP or HTTPS notifications targeted at your independent systems and synchronize traces received by CTS to your own audit systems for auditing.

   You can also select a certain type of log (such as file upload) as a trigger for a preset workflow (for example, file format conversion) in FunctionGraph, simplifying service deployment and O&M as well as preventing risks.

-  **Data value mining**

   CTS mines data in traces to facilitate service health analysis, risk analysis, resource tracking, and cost analysis. You can also obtain the data from CTS and explore the data value yourself.

   A trace contains extensive information, including the time, operator, operation device IP address, operated resource, and operation details. Each trace is worth mining.

   By configuring HTTP or HTTPS notifications, you can synchronize traces to your own system for analysis. In addition, CTS is connected to Cloud Eye and Log Tank Service (LTS) to help you monitor high-risk operations, detect unauthorized operations, and analyze resource usage.

-  **Fault locating and analysis**

   You can configure filters to pinpoint the faulty operation and its details when a fault occurs, reducing the time and workforce required for detecting, locating, and fixing faults.

   If a specific resource or action encounters a fault, you can query operation records on the resource in a specific time period and view the requests and responses to facilitate fault locating.

   CTS provides the following search dimensions: trace type, trace source, resource type, filter, operator and trace status. Each trace contains the request and response of an operation. Querying traces is one of the most efficient methods for locating a fault.

   If a problem occurs on the cloud, you can configure filters to search for all suspicious operations in a specified time period. You can then synchronize the relevant traces to O&M and customer service personnel who will handle the problem.
