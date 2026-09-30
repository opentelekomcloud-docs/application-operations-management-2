:original_name: DeleteMuteRulesPost.html

.. _DeleteMuteRulesPost:

Deleting a Silence Rule
=======================

Function
--------

This API is used to delete a silence rule.

Calling Method
--------------

For details, see :ref:`Calling APIs <aom_04_0057>`.

URI
---

POST /v2/{project_id}/alert/mute-rules/delete

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
   | Content-Type    | Yes             | String          | Message body type or format, which is **application/json**.                            |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | Enumeration values:                                                                    |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | -  **application/json**                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+

.. table:: **Table 3** Request body parameters

   +-----------+-----------+---------------------------------------------------------------------------------------------------------------------------+---------------------------------+
   | Parameter | Mandatory | Type                                                                                                                      | Description                     |
   +===========+===========+===========================================================================================================================+=================================+
   | [items]   | Yes       | Array of :ref:`DeleteMuteRuleName <deletemuterulespost__en-us_topic_0000002366852497_request_deletemuterulename>` objects | Name of the rule to be deleted. |
   +-----------+-----------+---------------------------------------------------------------------------------------------------------------------------+---------------------------------+

.. _deletemuterulespost__en-us_topic_0000002366852497_request_deletemuterulename:

.. table:: **Table 4** DeleteMuteRuleName

   ========= ========= ====== =======================================
   Parameter Mandatory Type   Description
   ========= ========= ====== =======================================
   name      Yes       String Name of the silence rule to be deleted.
   ========= ========= ====== =======================================

Response Parameters
-------------------

**Status code: 204**

No Content: The request is successful, but no content is returned.

**Status code: 400**

.. table:: **Table 5** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   error_type String Error type.
   trace_id   String Request ID.
   ========== ====== ==============

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

Delete silent rule "1112222".

.. code-block::

   https://{Endpoint}/v2/{project_id}/alert/mute-rules/delete

   [ {
     "name" : "1112222"
   } ]

Example Responses
-----------------

**Status code: 400**

Bad Request: Invalid request. The client should not repeat this request without modification.

.. code-block::

   {
     "error_code" : "AOM.08043002",
     "error_msg" : "the muteName is not exist",
     "error_type" : "PARAM_INVALID",
     "trace_id" : ""
   }

**Status code: 401**

Unauthorized: The authorization information provided by the client is incorrect or invalid.

.. code-block::

   {
     "error_code" : "AOM.0403",
     "error_msg" : "auth failed.",
     "error_type" : "AUTH_FAILED",
     "trace_id" : null
   }

**Status code: 403**

Forbidden: The request is rejected. The server has received the request and understood it, but the server is refusing to respond to it. The client should not repeat this request without modification.

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
     "error_code" : "AOM.08001500",
     "error_message" : "internal server error",
     "error_type" : "INTERNAL_SERVER_ERROR",
     "trace_id" : ""
   }

Status Codes
------------

+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                                                                                             |
+=============+=========================================================================================================================================================================================================+
| 204         | No Content: The request is successful, but no content is returned.                                                                                                                                      |
+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 400         | Bad Request: Invalid request. The client should not repeat this request without modification.                                                                                                           |
+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 401         | Unauthorized: The authorization information provided by the client is incorrect or invalid.                                                                                                             |
+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 403         | Forbidden: The request is rejected. The server has received the request and understood it, but the server is refusing to respond to it. The client should not repeat this request without modification. |
+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 500         | Internal Server Error: The server is able to receive the request but unable to understand the request.                                                                                                  |
+-------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
