:original_name: cts_03_0014.html

.. _cts_03_0014:

Digest Files
============

Overview
--------

A digest file contains the names and hash values of the trace files transferred to an OBS bucket an hour ago as well as the digital signature of the previous digest file. The digital signature of this digest file is stored in metadata attributes of the digest file object. A digest file is stored in the following path:

*OBS bucket name*\ **/CloudTraces/**\ *Region*\ **/**\ *Year*\ **/**\ *Month*\ **/**\ *Day*\ **/**\ *Tracker name*\ **/Digest/**\ *Cloud service*

Example: *OBS bucket name*\ **/CloudTraces/**\ *Region*\ **/2016/5/19/system/Digest/ECS**

Digest File Name Format
-----------------------

The digest files are named as follows:

*Trace file prefix*\ **\_CloudTrace-Digest\_**\ *Region/Region-Project*\ \_\ *Time when the digest file was sent to OBS:* *Year-Month-Day*\ **T**\ *Hour-Minute-Second* **Z.json.gz**

Example: *File Prefix*\ **\_CloudTrace-Digest\_**\ *region/region-project*\ **\_2016-05-30T16-20-56Z.json.gz**

Digest File Structure
---------------------

.. _cts_03_0014__en-us_topic_0170932673_table20698075144837:

.. table:: **Table 1** Key fields of a digest file

   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | Field                          | Mandatory | Type    | Description                                                                      |
   +================================+===========+=========+==================================================================================+
   | project_id                     | Yes       | String  | Identifies the account to which a trace file covered in the digest file belongs. |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | digest_start_time              | Yes       | String  | Specifies the start of the UTC time range covered by the digest file.            |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | digest_end_time                | Yes       | String  | Specifies the end of the UTC time range covered by the digest file.              |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | digest_bucket                  | Yes       | String  | Specifies the name of the OBS bucket that the digest file has been sent to.      |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | digest_object                  | Yes       | String  | Specifies where the digest file is stored in the OBS bucket.                     |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | digest_signature_algorithm     | Yes       | String  | Specifies the algorithm used to sign the digest file.                            |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | digest_end                     | Yes       | Boolean | Specifies whether the digest file is an ending digest file.                      |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | previous_digest_bucket         | No        | String  | Specifies the name of the OBS bucket that the previous digest file was sent to.  |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | previous_digest_object         | No        | String  | Specifies where the previous digest file is stored in the OBS bucket.            |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | previous_digest_hash_value     | No        | String  | Specifies the hexadecimal encoded hash value of the previous digest file.        |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | previous_digest_hash_algorithm | No        | String  | Specifies the Hash algorithm used to hash the previous digest file.              |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | previous_digest_signature      | No        | String  | Specifies the digital signature of the previous digest file.                     |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | previous_digest_end            | Yes       | Boolean | Specifies whether the previous digest file is an ending digest file.             |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | log_files                      | No        | Array   | Specifies the list of trace files covered in the digest file.                    |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | bucket                         | Yes       | String  | Specifies the name of the OBS bucket that the trace files have been sent to.     |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | object                         | Yes       | String  | Specifies where the trace files are stored in the OBS bucket.                    |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | log_hash_value                 | Yes       | String  | Specifies the hexadecimal encoded hash value of the trace files.                 |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+
   | log_hash_algorithm             | Yes       | String  | Specifies the Hash algorithm used to hash the trace files.                       |
   +--------------------------------+-----------+---------+----------------------------------------------------------------------------------+

Example Digest File
-------------------

A digest file contains the names and hash values of the trace files transferred to an OBS bucket an hour ago as well as the digital signature of the previous digest file. The digital signature of this digest file is stored in metadata attributes of the digest file object. A digest file is stored in the following path:

The following is an example digest file:

For details about the fields in the example, see :ref:`Table 1 <cts_03_0014__en-us_topic_0170932673_table20698075144837>`.

.. code-block::

   {
    "project_id": "3cfb09080bd944d0b4cdd72ef2685712",
    "digest_start_time": "2017-03-28T01-09-17Z",
    "digest_end_time": "2017-03-28T02-09-17Z",
    "digest_bucket": "bucket",
    "digest_object": "CloudTraces/eu-ch2a/2017/3/28/Digest/EVS/mylog_CloudTrace-Digest_eu-ch2a/_2017-03-28T02-09-17Z.json.gz",
    "digest_signature_algorithm": "SHA256withRSA",
    "digest_end": false,
    "previous_digest_bucket": "bucket",
    "previous_digest_object": "CloudTraces/eu-ch2a/2017/3/28/Digest/EVS/mylog_CloudTrace-Digest_eu-ch2a/_2017-03-28T01-09-17Z.json.gz",
    "previous_digest_hash_value": "5e08875de01b894eda5d1399d7b049fe",
    "previous_digest_hash_algorithm": "MD5",
    "previous_digest_signature": "7af7cbef4f3c78eab5048030d402810841400cf70eb22f93d4fedd13b13a8208a5dc04ce2f8bd0a4918f933ca3fcb17595ae59386a2dc3e3046fa97688a9815a2d036fa10193534c0ebbecff67221e22ac9cf8b781cbae3a81eaccfc0a2bd1a99081b1e4fe99b19caa771876ba7cce16d002feb4578cd89bc6f1faaca639ab48f3cb56007bcc5e248968f4a17a95b8cdbc7d8bbd7c63630da878cd4d471fc75c60bac5f730d94fefe8fdd2f2fa8accd62dbe100eab7773e7915e91be4474291b9dacea63a8267390bcb4855b5825554ebb07d4a29ce077c364213c575c461d1e9fafa0c29fde1c6de1d5630e015200821b2f3ae91e53cd8591433dd7c0b4c8bc",
    "previous_digest_end": false,
    "log_files": [{
     "bucket": "bucket",
     "object": "CloudTraces/eu-ch2a/2017/3/28/ECS/mylog_CloudTrace_eu-ch2a/_2017-03-28T02-09-17Z_0faa86bc40071242.json.gz",
     "log_hash_value": "633a8256ae7996e21430c3a0e9897828",
     "log_hash_algorithm": "MD5"
    }]
   }

Digest File Signature
---------------------

The digital signature information of a digest file is in two metadata attributes of the digest file object. Each digest file has the following two metadata items:

-  meta-signature

   Hexadecimal encoded value of the digest file signature. Example:

   .. code-block::

      7af7cbef4f3c78eab5048030d402810841400cf70eb22f93d4fedd13b13a8208a5dc04ce2f8bd0a4918f933ca3fcb17595ae59386a2dc3e3046fa97688a9815a2d036fa10193534c0ebbecff67221e22ac9cf8b781cbae3a81eaccfc0a2bd1a99081b1e4fe99b19caa771876ba7cce16d002feb4578cd89bc6f1faaca639ab48f3cb56007bcc5e248968f4a17a95b8cdbc7d8bbd7c63630da878cd4d471fc75c60bac5f730d94fefe8fdd2f2fa8accd62dbe100eab7773e7915e91be4474291b9dacea63a8267390bcb4855b5825554ebb07d4a29ce077c364213c575c461d1e9fafa0c29fde1c6de1d5630e015200821b2f3ae91e53cd8591433dd7c0b4c8bc

-  meta-signature-algorithm

   Algorithm used to sign the digest file. Example:

   SHA256withRSA

Supplementary Information
-------------------------

-  Starting Digest File

   A starting digest file is generated after you start verifying trace file integrity. In a starting digest file, the following fields related to the previous digest file will be left empty:

   -  previous_digest_bucket
   -  previous_digest_object
   -  previous_digest_hash_value
   -  previous_digest_hash_algorithm
   -  previous_digest_signature

-  "Empty" Digest File

   CTS will still send a digest file even if no operations have occurred in your account within the one-hour time period recorded by the digest file. The last field **log_files:[]** of the digest file will be left empty. It helps you to confirm that no trace files have been sent within the one-hour time period recorded by the digest file.

-  Digest File Chain

   A digest file contains the digital signature and Hash value of the previous digest file (if any) so that a chain is formed. You can verify digest files successively within a specified time, starting with the latest one.

-  Digest File Bucket

   A digest file is sent to the OBS bucket that stores trace files recorded in the file.

-  Digest File Storage Folder

   A digest file is stored in a folder different from that for trace files, making it easy for you to execute fine-grained security policies.
