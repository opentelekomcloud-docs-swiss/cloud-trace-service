:original_name: cts_faq_012.html

.. _cts_faq_012:

Why Is an Operation Recorded Twice in the Trace List?
=====================================================

For an asynchronously invoked trace, such as **deleteDesktop** trace of Workspace, two records with the same trace name, resource type, and resource name will be generated. The two records may seem to be the same. However, they are generated at different times and document different details.

-  The first record documents the request initiated by a user.
-  The second record documents the response to the request and the operation result, and is usually several minutes later than the first record.

The two records together give a full view of the operation.
