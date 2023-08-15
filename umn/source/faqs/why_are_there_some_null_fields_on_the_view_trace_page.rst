:original_name: cts_faq_010.html

.. _cts_faq_010:

Why Are There Some Null Fields on the View Trace Page?
======================================================

Fields **source_ip**, **code**, **request**, **response**, and **message** can be null. These fields are not mandatory for CTS.

-  **source_ip**: If the value of **trace_type** is **SystemAction**, the operation was triggered by the system. In this case, **source_ip** is null.
-  **request**, **response**, and **code**: These three fields indicate the request content, request result, and HTTP return code of an operation. In some cases, these fields are null or have no service meaning. Therefore, they are left blank based on actual situations.
-  **message**: This is a reserved field. Information of other cloud services will be added to this field when necessary. It is normal that the field is null.
