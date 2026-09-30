:original_name: AddActionRule.html

.. _AddActionRule:

Adding an Alarm Action Rule
===========================

Function
--------

This API is used to add an alarm action rule.

Calling Method
--------------

For details, see :ref:`Calling APIs <aom_04_0057>`.

URI
---

POST /v2/{project_id}/alert/action-rules

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

   +-----------------------+-----------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter             | Mandatory       | Type                                                                                              | Description                                                                                                                                                                            |
   +=======================+=================+===================================================================================================+========================================================================================================================================================================================+
   | rule_name             | Yes             | String                                                                                            | Alarm notification rule name. Enter a maximum of 100 characters and do not start or end with a special character. Only letters, digits, and underscores (_) are allowed.               |
   +-----------------------+-----------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | project_id            | Yes             | String                                                                                            | Project ID.                                                                                                                                                                            |
   +-----------------------+-----------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | user_name             | Yes             | String                                                                                            | Member account name.                                                                                                                                                                   |
   +-----------------------+-----------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | desc                  | No              | String                                                                                            | Rule description. Enter a maximum of 1,024 characters and do not start or end with an underscore (*). Only digits, letters, underscores (*), asterisk (``*``), and spaces are allowed. |
   +-----------------------+-----------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type                  | Yes             | String                                                                                            | Rule type.                                                                                                                                                                             |
   |                       |                 |                                                                                                   |                                                                                                                                                                                        |
   |                       |                 |                                                                                                   | -  1: Prometheus monitoring.                                                                                                                                                           |
   |                       |                 |                                                                                                   |                                                                                                                                                                                        |
   |                       |                 |                                                                                                   | -  3: Log monitoring.                                                                                                                                                                  |
   +-----------------------+-----------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | notification_template | Yes             | String                                                                                            | Message template.                                                                                                                                                                      |
   +-----------------------+-----------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | create_time           | No              | Long                                                                                              | Creation time (UTC timestamp, in milliseconds). Example: 2024-10-16 16:03:01 needs to be converted to UTC timestamp 1702759381000 using a tool.                                        |
   +-----------------------+-----------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | update_time           | No              | Long                                                                                              | Modification time (UTC timestamp, in milliseconds). Example: 2024-10-16 16:03:01 needs to be converted to UTC timestamp 1702759381000 using a tool.                                    |
   +-----------------------+-----------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | time_zone             | No              | String                                                                                            | Time zone.                                                                                                                                                                             |
   +-----------------------+-----------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | smn_topics            | Yes             | Array of :ref:`SmnTopics <addactionrule__en-us_topic_0000001557311954_request_smntopics>` objects | SMN topic. Max.: 5.                                                                                                                                                                    |
   +-----------------------+-----------------+---------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _addactionrule__en-us_topic_0000001557311954_request_smntopics:

.. table:: **Table 4** SmnTopics

   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                       |
   +=================+=================+=================+===================================================================================================================================================+
   | display_name    | No              | String          | Topic display name, which will be the name of an email sender. Max.: 192 bytes. This parameter is left blank by default.                          |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | name            | Yes             | String          | Name of the topic. Enter 1 to 255 characters starting with a letter or digit. Only letters, digits, hyphens (-), and underscores (_) are allowed. |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | push_policy     | Yes             | Integer         | SMN message push policy. Options: **0** and **1**.                                                                                                |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | status          | No              | Integer         | Status of the topic subscriber.                                                                                                                   |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  0: The topic has been deleted or the subscription list of this topic is empty.                                                                 |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  1: The subscription object is in the subscribed state.                                                                                         |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  2: The subscription object is in the unsubscribed or canceled state.                                                                           |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | Enumeration values:                                                                                                                               |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **0**                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **1**                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                   |
   |                 |                 |                 | -  **2**                                                                                                                                          |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+
   | topic_urn       | Yes             | String          | Unique resource identifier of the topic.                                                                                                          |
   +-----------------+-----------------+-----------------+---------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

OK: Operation successful.

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Response code.
   error_msg  String Response message.
   trace_id   String Response ID.
   ========== ====== =================

**Status code: 401**

.. table:: **Table 6** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   error_type String Error type.
   trace_id   String Request ID.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 7** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   error_type String Error type.
   trace_id   String Request ID.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 8** Response body parameters

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Response code.
   error_msg  String Response message.
   trace_id   String Response ID.
   ========== ====== =================

Example Requests
----------------

Add an alarm action rule whose name is "66666", username is "kxxxxxxxt", user ID is "21axxxxxxxxxxxxxxxxx47c", and notification template is "aom.built-in.template.en".

.. code-block::

   https://{Endpoint}/v2/{project_id}/alert/action-rules

   {
     "desc" : "1111",
     "notification_template" : "aom.built-in.template.zh",
     "project_id" : "21axxxxxxxxxxxxxxxxx47c",
     "rule_name" : "66666",
     "smn_topics" : [ {
       "display_name" : "",
       "name" : "xiaohama",
       "push_policy" : 0,
       "status" : 0,
       "topic_urn" : "urn:smn:xxx:21axxxxxxxxxxxxxxxxx47c:xiaohama"
     } ],
     "type" : "1",
     "user_name" : "kxxxxxxxt",
     "time_zone" : "xxx"
   }

Example Responses
-----------------

**Status code: 400**

Bad Request: Invalid request. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "AOM.08018012",
     "error_msg" : "actionRule already exists",
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
| 200         | OK: Operation successful.                                                                                                                                                                           |
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
