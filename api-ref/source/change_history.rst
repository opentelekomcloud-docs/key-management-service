:original_name: kms_02_0304.html

.. _kms_02_0304:

Change History
==============

+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Release Date                      | Description                                                                                                                                                       |
+===================================+===================================================================================================================================================================+
| 2025-11-19                        | This is the thirtieth official release.                                                                                                                           |
|                                   |                                                                                                                                                                   |
|                                   | Modified the URI in "Querying CMK Instances".                                                                                                                     |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-10-28                        | This is the twenty-ninth official release.                                                                                                                        |
|                                   |                                                                                                                                                                   |
|                                   | Added request examples in "Deleting a CMK Tag".                                                                                                                   |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-10-15                        | This is the twenty-eighth official release.                                                                                                                       |
|                                   |                                                                                                                                                                   |
|                                   | Added the **sys_tags** response parameter in "Querying CMK Tags".                                                                                                 |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-08-05                        | This is the twenty-seventh official release.                                                                                                                      |
|                                   |                                                                                                                                                                   |
|                                   | -  Deleted the **Content-Type** parameter for querying the number of instances, querying quotas, querying key tags, querying project tags, and deleting key tags. |
|                                   | -  Deleted the **sequence** parameter for deleting key tags.                                                                                                      |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-07-30                        | This is the twenty-sixth official release.                                                                                                                        |
|                                   |                                                                                                                                                                   |
|                                   | -  Changed the rotation interval of a CMK and removed the table "Request header parameters".                                                                      |
|                                   | -  Updated the table name as "URI parameter".                                                                                                                     |
|                                   | -  Moved APIs for querying the API version to separate folders.                                                                                                   |
|                                   | -  **Content-Type** is changed to not mandatory in "Querying the Aliases Associated with a Key".                                                                  |
|                                   | -  Deleted section "Alias Management" and APIs for associating an alias with a key and querying the aliases associated with a key.                                |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-07-25                        | This is the twenty-fifth official release.                                                                                                                        |
|                                   |                                                                                                                                                                   |
|                                   | -  Replace the example of URN on kms:eu-de-ring0:3ba44455500dd43127:alias:4555                                                                                    |
|                                   | -  Added example values for the **marker** parameter.                                                                                                             |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-07-23                        | This is the twenty-fourth official release.                                                                                                                       |
|                                   |                                                                                                                                                                   |
|                                   | Added APIs about secret management.                                                                                                                               |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-06-25                        | This is the twenty-third official release.                                                                                                                        |
|                                   |                                                                                                                                                                   |
|                                   | Deleted APIs for creating and deleting key aliases.                                                                                                               |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-06-19                        | This is the twenty-second official release.                                                                                                                       |
|                                   |                                                                                                                                                                   |
|                                   | -  Added parameters **X-Auth-Token** and **Content-Type** for all APIs.                                                                                           |
|                                   | -  Provide example of value and what is default value of parameter marker.                                                                                        |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-05-16                        | This is the twenty-first official release.                                                                                                                        |
|                                   |                                                                                                                                                                   |
|                                   | -  Moved **MAC** and **Alias Management** folders to the same level as the **CMK Management** folder.                                                             |
|                                   | -  The mandatory Content-Type parameter is added to the header parameter of Authenticating a Signature.                                                           |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-03-28                        | This is the twentieth official release.                                                                                                                           |
|                                   |                                                                                                                                                                   |
|                                   | -  Set the **Content-Type** parameter to mandatory in POST and PUT requests.                                                                                      |
|                                   | -  Modified the response parameters in "Querying the Aliases Associated with a Key".                                                                              |
|                                   | -  Added restriction description for the **mac_algorithm** parameter in "MAC".                                                                                    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-03-26                        | This is the nineteenth official release.                                                                                                                          |
|                                   |                                                                                                                                                                   |
|                                   | -  Modified section "Alias Management" and optimized the description of the **X-Auth-Token** parameter.                                                           |
|                                   | -  Modified the description of the alias example.                                                                                                                 |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-03-17                        | This is the eighteenth official release.                                                                                                                          |
|                                   |                                                                                                                                                                   |
|                                   | Modified the description about parameters **key_id** and **descriptionid**.                                                                                       |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2025-02-18                        | This is the seventeenth official release.                                                                                                                         |
|                                   |                                                                                                                                                                   |
|                                   | -  Added section "Alias Management".                                                                                                                              |
|                                   | -  Added section "Querying a Public Key".                                                                                                                         |
|                                   | -  Added section "MAC".                                                                                                                                           |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2024-03-25                        | This is the sixteenth official release.                                                                                                                           |
|                                   |                                                                                                                                                                   |
|                                   | -  Optimized the description of the **grantee_principal_type** parameter in section "Creating a Grant".                                                           |
|                                   | -  Added an example of the **message_type** in section "Signing Data".                                                                                            |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2023-11-29                        | This is the fifteenth official release.                                                                                                                           |
|                                   |                                                                                                                                                                   |
|                                   | Modified the description of some API request parameters in section "API Description".                                                                             |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2023-10-20                        | This is the fourteenth official release.                                                                                                                          |
|                                   |                                                                                                                                                                   |
|                                   | -  Added section "Signing Data".                                                                                                                                  |
|                                   | -  Added section "Authenticating a Signature".                                                                                                                    |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2022-09-30                        | This is the thirteenth official release.                                                                                                                          |
|                                   |                                                                                                                                                                   |
|                                   | Optimized descriptions in sections "Permissions Policies and Supported Actions".                                                                                  |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2021-10-20                        | This is the twelfth official release.                                                                                                                             |
|                                   |                                                                                                                                                                   |
|                                   | -  Added section "Permissions and Supported Actions".                                                                                                             |
|                                   | -  Added description about default KMS performance thresholds in "CMK Management".                                                                                |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2021-09-22                        | This is the eleventh official release.                                                                                                                            |
|                                   |                                                                                                                                                                   |
|                                   | Modified the error code format in the "Error Codes" section.                                                                                                      |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2019-12-10                        | This is the tenth official release.                                                                                                                               |
|                                   |                                                                                                                                                                   |
|                                   | -  Added section "Enabling Rotation for a CMK".                                                                                                                   |
|                                   | -  Added section "Changing the Rotation Interval for a CMK".                                                                                                      |
|                                   | -  Added section "Disabling Rotation for a CMK".                                                                                                                  |
|                                   | -  Added section "Querying the Rotation Status of a CMK".                                                                                                         |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2019-03-13                        | This is the ninth official release.                                                                                                                               |
|                                   |                                                                                                                                                                   |
|                                   | Added section "API Permissions".                                                                                                                                  |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2018-09-30                        | This is the eighth official release.                                                                                                                              |
|                                   |                                                                                                                                                                   |
|                                   | -  Added section "Querying All API Versions."                                                                                                                     |
|                                   | -  Added section "Querying a Specified API Version."                                                                                                              |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2018-07-30                        | This is the seventh official release.                                                                                                                             |
|                                   |                                                                                                                                                                   |
|                                   | -  Modified section "Error Codes": added error codes KMS.0417, KMS.0418, and their descriptions.                                                                  |
|                                   | -  Modified the descriptions about status codes returned following each request. The normal status codes and exception status codes are described separately.     |
|                                   | -  Modified section "Status Codes": added status code **204** and its description.                                                                                |
|                                   | -  Modified the description of the **resource_detail** parameter in section "Querying CMK Instances".                                                             |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2018-03-30                        | This is the sixth official release.                                                                                                                               |
|                                   |                                                                                                                                                                   |
|                                   | -  Added section "Obtaining CMK Import Parameters".                                                                                                               |
|                                   | -  Added section "Importing CMK Material".                                                                                                                        |
|                                   | -  Added section "Deleting CMK Material".                                                                                                                         |
|                                   | -  Added section "Querying CMK Instances".                                                                                                                        |
|                                   | -  Added section "Querying CMK Tags".                                                                                                                             |
|                                   | -  Added section "Querying Project Tags".                                                                                                                         |
|                                   | -  Added section "Adding or Deleting CMK Tags in Batches".                                                                                                        |
|                                   | -  Added section "Adding a CMK Tag".                                                                                                                              |
|                                   | -  Added section "Deleting a CMK Tag".                                                                                                                            |
|                                   | -  Optimized error codes and modified section "Error Codes".                                                                                                      |
|                                   |                                                                                                                                                                   |
|                                   |    -  Added error codes KMS.0309, KMS.0310, and KMS.0401-KMS.0413 to the common error codes.                                                                      |
|                                   |    -  Added error codes and their description for importing CMK material.                                                                                         |
|                                   |    -  Added error codes and their description for deleting CMK material.                                                                                          |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2017-10-30                        | This is the fifth official release.                                                                                                                               |
|                                   |                                                                                                                                                                   |
|                                   | -  Added section "Creating a Grant".                                                                                                                              |
|                                   | -  Added section "Revoking a Grant".                                                                                                                              |
|                                   | -  Added section "Retiring a Grant".                                                                                                                              |
|                                   | -  Added section "Querying Grants on a CMK".                                                                                                                      |
|                                   | -  Added section "Querying Grants that Can Be Retired".                                                                                                           |
|                                   | -  Optimized request parameter description in section "Creating a CMK".                                                                                           |
|                                   | -  Optimized request and response parameter description in section "Querying the List of CMKs".                                                                   |
|                                   | -  Optimized response parameter description in section "Querying the Information About a CMK".                                                                    |
|                                   | -  Optimized response parameter description in section "Creating a Random Number".                                                                                |
|                                   | -  Optimized response parameter description in section "Querying the Quota of a User".                                                                            |
|                                   | -  Optimized error codes and modified section "Error Codes".                                                                                                      |
|                                   |                                                                                                                                                                   |
|                                   |    -  Added public error code KMS.0308 and its description.                                                                                                       |
|                                   |    -  Added error codes and their description for creating a grant.                                                                                               |
|                                   |    -  Added error codes and their description for querying grants on a CMK.                                                                                       |
|                                   |    -  Added error codes and their description for querying grants that can be retired.                                                                            |
|                                   |    -  Added error codes and their description for revoking a grant.                                                                                               |
|                                   |    -  Added error codes and their description for retiring a grant.                                                                                               |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2017-06-30                        | This is the fourth official release.                                                                                                                              |
|                                   |                                                                                                                                                                   |
|                                   | -  Added sections "Changing the Alias of a CMK" and "Changing the Description of a CMK".                                                                          |
|                                   | -  Optimized the type of parameter **keys** in section "Querying the List of CMKs".                                                                               |
|                                   | -  Optimized response parameter tables in sections "Querying the Number of Instances" and "Querying Quotas".                                                      |
|                                   | -  Optimized error codes and modified section "Error Codes".                                                                                                      |
|                                   |                                                                                                                                                                   |
|                                   |    -  Added error codes and their description for changing the alias of a CMK.                                                                                    |
|                                   |    -  Added error codes and their description for changing the description of a CMK.                                                                              |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2017-02-08                        | This is the third official release.                                                                                                                               |
|                                   |                                                                                                                                                                   |
|                                   | Added sections "Querying the Number of Instances" and "Querying Quotas".                                                                                          |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2016-12-30                        | This is the second official release.                                                                                                                              |
|                                   |                                                                                                                                                                   |
|                                   | -  Optimized error codes and modified section "Error Codes".                                                                                                      |
|                                   | -  Added description about parameter **encryption_context** to the following sections:                                                                            |
|                                   |                                                                                                                                                                   |
|                                   |    -  "Creating a DEK"                                                                                                                                            |
|                                   |    -  "Creating a Plaintext-Free DEK"                                                                                                                             |
|                                   |    -  "Encrypting a DEK"                                                                                                                                          |
|                                   |    -  "Decrypting a DEK"                                                                                                                                          |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 2016-10-29                        | This is the first official release.                                                                                                                               |
+-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------+
