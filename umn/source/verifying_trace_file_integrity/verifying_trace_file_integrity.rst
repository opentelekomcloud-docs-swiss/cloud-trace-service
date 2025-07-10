:original_name: cts_03_0021.html

.. _cts_03_0021:

Verifying Trace File Integrity
==============================

Scenarios
---------

CTS uses public signature algorithms and hash functions in accordance with industry standards, so you can create tools on your own to verify integrity of CTS trace files. Trace files should contain fields **time**, **service_type**, **resource_type**, **trace_name**, **trace_rating**, and **trace_type** for integrity verification. Other fields can be added by services from which traces are collected.

After you enable integrity verification of trace files in CTS, digest files will be sent to your OBS buckets, and you can implement your own verification solution. For details about digest files, see :ref:`Digest Files <cts_03_0014>`.

Prerequisites
-------------

You should understand how digest files are signed.

RSA digital signatures are used in CTS. For each digest file, CTS will:

#. Create a message for digital signing, a character string composed of specified digest file fields, and obtain an RSA private key.
#. Produce a hash value of the digest message. Use the RSA algorithm to generate a digital signature with the hash value and private key, and encode the digital signature to hexadecimal format.
#. Put the digital signature into the meta-signature attribute of the digest file object.

The message for digital signing contains the following digest file fields:

-  The ending timestamp of the UTC time range covered by the digest file, for example, 2017-03-28T02-09-17Z.
-  The path where the current digest file is stored in the OBS bucket.
-  The hash value (hexadecimal encoded) of the current digest file (compressed).
-  The hexadecimal digital signature of the previous digest file.


Verifying Trace File Integrity
------------------------------

Verify a digest file first and then its referenced trace files.

#. Obtain a digest file.

   a. Obtain the latest digest file within the time range to be verified from the OBS bucket.
   b. Check whether the location where the digest file is stored in the OBS bucket matches with the location recorded in the file.
   c. Obtain the digital signature from the meta-signature attribute of the digest file object.

#. Obtain the RSA public key for verifying the digital signature.

   The RSA public key of CTS is as follows:

   .. code-block::

      MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAsjQDkl8COPRhOCvm7ZI8sYZ20ojl+ay/gwRSk9q0gkY3pP0RrAhSsEzgYdYjaMCqixkmbpt4AH9AROJU4drnoCAZSMqRxgv0bGC9kVd4q95l4zibswAsksjuNQo/XoJjBl+rRAqCa+1uetgVU4k4Yx8RryYxYx/tImvMe/O4mGAIaTf+rsqt3VXR1QIj5lYR/nx41BEgC/Kb1elYAfDaaab8WS5INRprj7qdu6oAo4Ug47WqbecvEtG3JRpj5+oqLyW41Fvse3osC0h5DQdxTt4x00/rVZ+gH7Kua00y7gC8YOxFVpYbfn/oW61PUDeHG/N9hUjOrIgDDJpD2YbCIQIDAQAB

#. .. _cts_03_0021__en-us_topic_0170932846_li1168729815024:

   Recreate the message for digital signing.

   Compute the message for digital signing.

   The message is in the following format:

   .. code-block::

      signature_string = digest_end_time
      + digest_object
      + Hex(hash(digest-file-content))
      + previous_digest_signature

   The following is an example message for digital signing.

   .. code-block::

      2017-03-28T02-09-17ZCloudTraces/eu-ch2a/2017/3/28/Digest/EVS/mylog_CloudTrace-Digest_eu-ch2a/_2017-03-28T02-09-17Z.json.gze280d203da44015e0eda3faa7a2ec9612221cc0dc8b0fe320db4febe60142350641ad19da18cb6d3f5e7faad792c3efe98836c6d6547f5e5c7a48f7088000a057af26cc3bb913cae1637befa9e4231b7d1fd6d98eaba735e509e7c5ea3c6757f732b4468f7418ef18e3312ac696dd786ec5792eacf94aee27cd7be76bf23b641c5e9a686cca6414745787254100c2bee31e584a15c2229270f9dee81f9043574

#. .. _cts_03_0021__en-us_topic_0170932846_li4993090715024:

   Verify a digest file.

   Pass the computed message obtained in :ref:`3 <cts_03_0021__en-us_topic_0170932846_li1168729815024>`, digital signature of the digest file, and public key to the RSA signature verification algorithm. If **true** is returned, the digital signature of the digest file matches with the computed message and the digest file is valid.

#. .. _cts_03_0021__en-us_topic_0170932846_li1787163015024:

   Verify trace files.

   You can verify trace files referenced by the digest file after confirming that the digest file is valid.

   The digest file records the hash value of each trace file. After a trace file is uploaded to OBS, its hash value will be stored in ETag metadata. If the trace file is modified after CTS sent it to an OBS bucket, the file's hash value will change, and the digital signatures of the digest file will not match.

   Do as follows to verify a trace file:

   a. Obtain **bucket** and **object** information about a trace file from the digest file.
   b. Call the OBS client interface to obtain the ETag metadata value in the trace file object header.
   c. Obtain the hash value of the trace file from the **log_hash_value** field in the digest file.
   d. Compare the ETag metadata value with the hash value obtained in the previous step. If they mach, the trace file is valid.

#. Verify the previous digest files and trace files.

   In each digest file, the following fields provide the location and signature of the previous digest file:

   -  previous_digest_bucket
   -  previous_digest_object
   -  previous_digest_signature

   Repeat steps :ref:`4 <cts_03_0021__en-us_topic_0170932846_li4993090715024>` and :ref:`5 <cts_03_0021__en-us_topic_0170932846_li1787163015024>` to verify the signature of each previous digest file and all trace files that the file references.

   For these previous digest files, you do not need to obtain the digital signature from the meta-signature attribute of the digest file object. The **previous_digest_signature** field in each digest file provides the digital signature of the previous digest file. You can keep verifying the previous digest files and their referenced trace files until you reach the starting digest file or the digest file chain is disconnected.

   The following code segment is an example for verifying CTS digest and trace files. The code segment uses the following JAR packages, and you are recommended to use these packages:

   -  esdk-obs-java-2.1.16.jar
   -  commons-logging-1.2.jar
   -  httpasyncclient-4.1.2.jar
   -  httpclient-4.5.3.jar
   -  httpcore-4.4.4.jar
   -  httpcore-nio-4.4.4.jar
   -  java-xmlbuilder-1.1.jar
   -  jna-4.1.0.jar
   -  log4j-api-2.8.2.jar
   -  log4j-core-2.8.2.jar
   -  commons-codec-1.9.jar
   -  json-20160810.jar
   -  commons-io-2.5.jar

   Example code segment:

   .. code-block::

      import java.io.BufferedInputStream;
      import java.io.BufferedReader;
      import java.io.ByteArrayInputStream;
      import java.io.InputStream;
      import java.io.InputStreamReader;
      import java.security.KeyFactory;
      import java.security.MessageDigest;
      import java.security.PublicKey;
      import java.security.Signature;
      import java.security.spec.X509EncodedKeySpec;
      import java.util.Arrays;
      import java.util.zip.GZIPInputStream;

      import org.apache.commons.codec.binary.Base64;
      import org.apache.commons.codec.binary.Hex;
      import org.apache.commons.io.IOUtils;
      import org.json.JSONObject;

      import com.obs.services.ObsClient;
      import com.obs.services.ObsConfiguration;
      import com.obs.services.model.ObjectMetadata;
      import com.obs.services.model.S3Object;

      public class DigestFileValidator {
          public static void main(String[] args) {
              // Name of the bucket where a digest file is located.
              String digestBucket = "bucketname";
              // Path where a digest file is stored. Example: CloudTraces/eu-de/2017/11/15/Digest/ECS/tGPYa_CloudTrace-Digest_eu-de_2017-11-15T10-12-10Z.json.gz.
              String digestObject = "digestObject";


              ObsConfiguration obsConfig = new ObsConfiguration();

              obsConfig.setEndPoint("***Provide OBS EndPoint ***");
              ObsClient client = new ObsClient(ak, sk, obsConfig);

              try {
                  // Obtain a digest file object.
                  S3Object object = client.getObject(digestBucket, digestObject);

                  InputStream is = new BufferedInputStream(object.getObjectContent());
                  byte[] digestFileBytes = IOUtils.toByteArray(is);

                  // Obtain the hash value of a digest file.
                  MessageDigest messageDigest = MessageDigest.getInstance("MD5");
                  messageDigest.update(digestFileBytes);
                  byte[] digestFileHashBytes = messageDigest.digest();

                  StringBuilder outStr = new StringBuilder();
                  GZIPInputStream gis = new GZIPInputStream(new ByteArrayInputStream(digestFileBytes));
                  BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(gis, "UTF-8"));
                  String line;
                  while ((line = bufferedReader.readLine()) != null) {
                      outStr.append(line);
                  }
                  bufferedReader.close();
                  String digestInfo = outStr.toString();

                  // Obtain the meta-signature value from the digest file header in an OBS bucket, which is the digital signature of the digest file.
                  ObjectMetadata objectMetadata = client.getObjectMetadata(digestBucket, digestObject);
                  String digestSignature = objectMetadata.getMetadata().get("meta-signature").toString();
                  JSONObject digestFile = new JSONObject(digestInfo);
                  // Check whether the digest file has been moved in the OBS bucket.
                  if (!digestFile.getString("digest_bucket").equals(digestBucket) || !digestFile.getString("digest_object")
                      .equals(digestObject)) {
                      System.err.println("Digest file has been moved from its original location.");
                  } else {
                      // Obtain the message for digital signing.
                      String signatureString = digestFile.getString("digest_end_time") + digestFile.getString("digest_object")
                          + Hex.encodeHexString(digestFileHashBytes) + digestFile.getString("previous_digest_signature");

                      String publicKeyString
                          = "MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAsjQDkl8COPRhOCvm7ZI8sYZ20ojl+ay/gwRSk9q0gkY3pP0RrAhSsEzgYdYjaMCqixkmbpt4AH9AROJU4drnoCAZSMqRxgv0bGC9kVd4q95l4zibswAsksjuNQo/XoJjBl+rRAqCa+1uetgVU4k4Yx8RryYxYx/tImvMe/O4mGAIaTf+rsqt3VXR1QIj5lYR/nx41BEgC/Kb1elYAfDaaab8WS5INRprj7qdu6oAo4Ug47WqbecvEtG3JRpj5+oqLyW41Fvse3osC0h5DQdxTt4x00/rVZ+gH7Kua00y7gC8YOxFVpYbfn/oW61PUDeHG/N9hUjOrIgDDJpD2YbCIQIDAQAB";

                      // Public key used for decryption.
                      byte[] publicKeyBytes = Base64.decodeBase64(publicKeyString);
                      // Form the X509EncodedKeySpec object.
                      X509EncodedKeySpec x509EncodedKeySpec = new X509EncodedKeySpec(publicKeyBytes);

                      // Specify a cryptographic algorithm.
                      KeyFactory keyFactory = KeyFactory.getInstance("RSA");
                      // Obtain the public key object.
                      PublicKey publicKey = keyFactory.generatePublic(x509EncodedKeySpec);

                      Signature signatureInstance = Signature.getInstance("SHA256withRSA");
                      signatureInstance.initVerify(publicKey);
                      signatureInstance.update(signatureString.getBytes("UTF-8"));

                      byte[] signatureHashExpect = Hex.decodeHex(digestSignature.toCharArray());

                      // Verify whether the signature is valid.
                      if (signatureInstance.verify(signatureHashExpect)) {
                          System.out.println("Digest file signature is valid, validating log files...");

                          for (int i = 0; i < digestFile.getJSONArray("log_files").length(); i++) {
                              JSONObject logFileJson = digestFile.getJSONArray("log_files").getJSONObject(i);
                              String logBucket = logFileJson.getString("bucket");
                              String logObject = logFileJson.getString("object");

                              // Obtain the ETag value from the trace file header in the OBS bucket, which is the recorded hash value of the trace file.
                              ObjectMetadata objectLogMetadata = client.getObjectMetadata(logBucket, logObject);
                              String logHashValue = objectLogMetadata.getMetadata().get("ETag").toString();
                              logHashValue = logHashValue.replace("\"", "");
                              byte[] logFileHash = Hex.decodeHex(logHashValue.toCharArray());

                              // Obtain the hash value of each trace file from the digest file.
                              byte[] expectedHash = logFileJson.getString("log_hash_value").getBytes();
                              boolean hashMatch = Arrays.equals(expectedHash, logFileHash);
                              if (!hashMatch) {
                                  System.err.println("Validate log file hash failed.");
                              } else {
                                  System.out.println("Log file hash is valid.");
                              }
                          }
                      } else {
                          System.err.println("Validate digest signature failed.");
                      }

                      System.out.println("Digest file validation completed.");

                      // Obtain values of fields previous_digest_bucket, previous_digest_object, and previous_digest_signature of the previous digest file. After obtaining the digest file, verify its hash value and digital signature.
                      String previousDigestBucket = digestFile.getString("previous_digest_bucket");
                      String previousDigestObject = digestFile.getString("previous_digest_object");

                      // Obtain the digital signature from the meta-signature attribute of the digest file object header.
                      ObjectMetadata objectPreviousMetadata = client.getObjectMetadata(previousDigestBucket,
                          previousDigestObject);
                      String signatruePrevious = objectPreviousMetadata.getMetadata().get("meta-signature").toString();
                      String signatruePreviousExpect = digestFile.getString("previous_digest_signature");
                      if (signatruePrevious.equals(signatruePreviousExpect)) {
                          System.out.println(
                              "Previous digest file signature is valid, " + "validating previous digest file hash value...");

                          String digestPreviousHashValue = objectPreviousMetadata.getMetadata().get("ETag").toString();
                          // The ETag metadata value is the trace file hash value enclosed with quotation marks. You need to remove the quotation marks.
                          String digestPreviousHashValueExpect = "\"" + digestFile.getString("previous_digest_hash_value")
                              + "\"";
                          if (digestPreviousHashValue.equals(digestPreviousHashValueExpect)) {
                              System.out.println("Previous digest file hash value is valid.");
                          } else {
                              System.err.println("Validate previous digest file hash value failed.");
                          }
                      }
                  }
              } catch (Exception e) {
                  System.out.println("Validate digest file failed.");
              }
          }
      }
