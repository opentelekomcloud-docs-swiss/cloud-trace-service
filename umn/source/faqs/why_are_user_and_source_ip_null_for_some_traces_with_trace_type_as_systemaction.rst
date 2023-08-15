:original_name: cts_faq_005.html

.. _cts_faq_005:

Why Are user and source_ip Null for Some Traces with trace_type as SystemAction?
================================================================================

The **trace_type** field indicates the request source. This field can be **ConsoleAction**, **ApiCall**, and **SystemAction**.

**SystemAction** indicates operations that are not triggered by users, such as alarms, elastic scaling, regular backup, or secondary invocations by systems to complete a user's request. In this case, **user** and **source_ip** are both null.
