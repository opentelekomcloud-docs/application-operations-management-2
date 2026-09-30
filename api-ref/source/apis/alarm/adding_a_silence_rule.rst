:original_name: AddMuteRules.html

.. _AddMuteRules:

Adding a Silence Rule
=====================

Function
--------

This API is used to add a silence rule.

Calling Method
--------------

For details, see :ref:`Calling APIs <aom_04_0057>`.

URI
---

POST /v2/{project_id}/alert/mute-rules

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                            |
   +============+===========+========+========================================================================================================================================+
   | project_id | Yes       | String | Project ID, which can be obtained from the console or by calling an API. For details, see :ref:`Obtaining a Project ID <aom_04_0024>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 2** Request header parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                            |
   +=================+=================+=================+========================================================================================+
   | X-Auth-Token    | Yes             | String          | User token obtained from IAM. For details, see :ref:`Obtaining a Token <aom_04_0059>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | Content-Type    | Yes             | String          | Message body type or format. Content type, which is application/json.                  |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | Enumeration values:                                                                    |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | -  **application/json**                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------------+-----------------+------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                                                     | Description                                                                                                                                                               |
   +=================+=================+==========================================================================================+===========================================================================================================================================================================+
   | create_time     | No              | Long                                                                                     | Time when the silence rule was created (UTC timestamp, in milliseconds). Example: 2024-10-16 16:03:01 needs to be converted to UTC timestamp 1702759381000 using a tool.  |
   +-----------------+-----------------+------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | desc            | No              | String                                                                                   | Rule description.                                                                                                                                                         |
   +-----------------+-----------------+------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | match           | Yes             | Array<Array<:ref:`Match <addmuterules__en-us_topic_0000001607752277_request_match>`>>    | Match condition of the rule. Up to 10 serial or parallel conditions can be created.                                                                                       |
   +-----------------+-----------------+------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | mute_config     | Yes             | :ref:`MuteConfig <addmuterules__en-us_topic_0000001607752277_request_muteconfig>` object | Time when the rule takes effect.                                                                                                                                          |
   +-----------------+-----------------+------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | Yes             | String                                                                                   | Rule name.                                                                                                                                                                |
   |                 |                 |                                                                                          |                                                                                                                                                                           |
   |                 |                 |                                                                                          | Enter a maximum of 100 characters and do not start or end with an underscore (_). Only letters, digits, and underscores are allowed.                                      |
   +-----------------+-----------------+------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timezone        | No              | String                                                                                   | Time zone.                                                                                                                                                                |
   +-----------------+-----------------+------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time     | No              | Long                                                                                     | Time when the silence rule was modified (UTC timestamp, in milliseconds). Example: 2024-10-16 16:03:01 needs to be converted to UTC timestamp 1702759381000 using a tool. |
   +-----------------+-----------------+------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_id         | No              | String                                                                                   | User ID.                                                                                                                                                                  |
   +-----------------+-----------------+------------------------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _addmuterules__en-us_topic_0000001607752277_request_match:

.. table:: **Table 4** Match

   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                       |
   +=================+=================+==================+===================================================================================================+
   | key             | Yes             | String           | Key specified in the metadata for matching.                                                       |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------+
   | operate         | Yes             | String           | Match mode. EXIST: Exist. REGEX: Regular expression. EQUALS: Equal to.                            |
   |                 |                 |                  |                                                                                                   |
   |                 |                 |                  | Enumeration values:                                                                               |
   |                 |                 |                  |                                                                                                   |
   |                 |                 |                  | -  **EQUALS**                                                                                     |
   |                 |                 |                  |                                                                                                   |
   |                 |                 |                  | -  **REGEX**                                                                                      |
   |                 |                 |                  |                                                                                                   |
   |                 |                 |                  | -  **EXIST**                                                                                      |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------+
   | value           | No              | Array of strings | Value corresponding to the key. If **operate** is set to **EXIST**, this parameter is left blank. |
   +-----------------+-----------------+------------------+---------------------------------------------------------------------------------------------------+

.. _addmuterules__en-us_topic_0000001607752277_request_muteconfig:

.. table:: **Table 5** MuteConfig

   +-----------------+-----------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type              | Description                                                                                                                                                                                                                   |
   +=================+=================+===================+===============================================================================================================================================================================================================================+
   | ends_at         | No              | Long              | End time of the silence rule (UTC timestamp, in milliseconds). If the silence rule is permanent, set this parameter to **0**. Example: 2024-10-16 16:03:01 needs to be converted to UTC timestamp 1702759381000 using a tool. |
   +-----------------+-----------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | scope           | No              | Array of integers | When **type** is set to **WEEKLY** or **MONTHLY**, **scope** cannot be empty.                                                                                                                                                 |
   +-----------------+-----------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | starts_at       | Yes             | Long              | Start time of the silence rule (UTC timestamp, in milliseconds). Example: 2024-10-16 16:03:01 needs to be converted to UTC timestamp 1702759381000 using a tool.                                                              |
   +-----------------+-----------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | Yes             | String            | Type of the time for the silence rule to take effect. FIXED: Fixed time. DAILY: Certain time every day. WEEKLY: Certain time every week. MONTHLY: Certain time every month.                                                   |
   |                 |                 |                   |                                                                                                                                                                                                                               |
   |                 |                 |                   | Enumeration values:                                                                                                                                                                                                           |
   |                 |                 |                   |                                                                                                                                                                                                                               |
   |                 |                 |                   | -  **FIXED**                                                                                                                                                                                                                  |
   |                 |                 |                   |                                                                                                                                                                                                                               |
   |                 |                 |                   | -  **DAILY**                                                                                                                                                                                                                  |
   |                 |                 |                   |                                                                                                                                                                                                                               |
   |                 |                 |                   | -  **WEEKLY**                                                                                                                                                                                                                 |
   |                 |                 |                   |                                                                                                                                                                                                                               |
   |                 |                 |                   | -  **MONTHLY**                                                                                                                                                                                                                |
   +-----------------+-----------------+-------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

No Content: The request is successful, but no content is returned.

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   error_type String Error type.
   trace_id   String Request ID.
   ========== ====== ==============

**Status code: 401**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   error_type String Error type.
   trace_id   String Request ID.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 8** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   error_type String Error type.
   trace_id   String Request ID.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 9** Response body parameters

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Response code.
   error_msg  String Response message.
   trace_id   String Response ID.
   ========== ====== =================

Example Requests
----------------

Add a silence rule whose name is "32255" and user ID is "2xxxxxxxxxxxxxxxxxxxxxxxxxcf".

.. code-block::

   https://{Endpoint}/v2/{project_id}/alert/mute-rules

   {
     "create_time" : 1668147671966,
     "desc" : "",
     "match" : [ [ {
       "key" : "event_severity",
       "operate" : "EQUALS",
       "value" : [ "Info" ]
     } ] ],
     "mute_config" : {
       "ends_at" : 86399,
       "scope" : [ ],
       "starts_at" : 0,
       "type" : "DAILY"
     },
     "name" : "32255",
     "timezone" : "xxx",
     "update_time" : 1668147671966,
     "user_id" : "2xxxxxxxxxxxxxxxxxxxxxxxxxcf"
   }

Example Responses
-----------------

**Status code: 400**

Bad Request: Invalid request. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "AOM.08011001",
     "error_msg" : "the muteName is exist",
     "error_type" : "PARAM_INVALID",
     "trace_id" : ""
   }

**Status code: 401**

Unauthorized: The authentication information is incorrect or invalid.

.. code-block::

   {
     "error_code" : "AOM.0403",
     "error_msg" : "auth failed.",
     "error_type" : "AUTH_FAILED",
     "trace_id" : null
   }

**Status code: 403**

Forbidden: The request is rejected. The server has received the request and understood it, but the server refuses to respond to it. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "AOM.0403",
     "error_msg" : "auth failed.",
     "error_type" : "AUTH_FAILED",
     "trace_id" : null
   }

**Status code: 500**

Internal Server Error: The server is able to receive the request but unable to understand the request.

.. code-block::

   {
     "error_code" : "APM.00000500",
     "error_msg" : "Internal Server Error",
     "trace_id" : ""
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                                                                                         |
+=============+=====================================================================================================================================================================================================+
| 204         | No Content: The request is successful, but no content is returned.                                                                                                                                  |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 400         | Bad Request: Invalid request. The client should not repeat the request without modifications.                                                                                                       |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 401         | Unauthorized: The authentication information is incorrect or invalid.                                                                                                                               |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 403         | Forbidden: The request is rejected. The server has received the request and understood it, but the server refuses to respond to it. The client should not repeat the request without modifications. |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 500         | Internal Server Error: The server is able to receive the request but unable to understand the request.                                                                                              |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
