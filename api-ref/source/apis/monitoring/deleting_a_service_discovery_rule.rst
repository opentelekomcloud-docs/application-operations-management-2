:original_name: DeleteserviceDiscoveryRules.html

.. _DeleteserviceDiscoveryRules:

Deleting a Service Discovery Rule
=================================

Function
--------

This API is used to delete a service discovery rule.

Calling Method
--------------

For details, see :ref:`Calling APIs <aom_04_0057>`.

URI
---

DELETE /v1/{project_id}/inv/servicediscoveryrules

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                   |
   +============+===========+========+===============================================================================+
   | project_id | Yes       | String | Project ID obtained from IAM. Generally, a project ID contains 32 characters. |
   +------------+-----------+--------+-------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-------------+-----------+-------+----------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type  | Description                                                                                        |
   +=============+===========+=======+====================================================================================================+
   | appRulesIds | Yes       | Array | Discovery rule ID. Multiple IDs need to be separated by commas (,). The parameter cannot be empty. |
   +-------------+-----------+-------+----------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                              |
   +=================+=================+=================+==========================================+
   | X-Auth-Token    | Yes             | String          | User token obtained from IAM.            |
   +-----------------+-----------------+-----------------+------------------------------------------+
   | Content-Type    | Yes             | String          | Content type, which is application/json. |
   |                 |                 |                 |                                          |
   |                 |                 |                 | Enumeration values:                      |
   |                 |                 |                 |                                          |
   |                 |                 |                 | -  **application/json**                  |
   +-----------------+-----------------+-----------------+------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +----------------+------------------+-------------------------------------------------------------------------------------------------------+
   | Parameter      | Type             | Description                                                                                           |
   +================+==================+=======================================================================================================+
   | errorCode      | String           | Response code.                                                                                        |
   +----------------+------------------+-------------------------------------------------------------------------------------------------------+
   | errorMessage   | String           | Response message.                                                                                     |
   +----------------+------------------+-------------------------------------------------------------------------------------------------------+
   | responseStatus | Integer          | Response status code (no longer used).                                                                |
   +----------------+------------------+-------------------------------------------------------------------------------------------------------+
   | id             | Array of strings | Service discovery rule ID list. This parameter is used during cross-AZ configuration synchronization. |
   +----------------+------------------+-------------------------------------------------------------------------------------------------------+

Example Requests
----------------

Delete a service discovery rule with a specified ID.

.. code-block::

   https://{Endpoint}/v1/{project_id}/inv/servicediscoveryrules?appRulesIds=b788349e-62b2-xxxx-xxxx-02c611d59801

Example Responses
-----------------

**Status code: 200**

OK: The request is successful.

.. code-block::

   {
     "errorCode" : "SVCSTG.INV.2000000",
     "errorMessage" : null,
     "id" : [ ]
   }

**Status code: 400**

Bad Request: The request is invalid. The client should not repeat the request without modifications.

.. code-block::

   {
     "errorCode" : "SVCSTG.INV.4000115",
     "errorMessage" : "Request param is invalid",
     "id" : [ ]
   }

**Status code: 404**

Not Found: The requested resource could not be found. The client should not repeat this request without modification.

.. code-block::

   {
     "errorCode" : "SVCSTG.INV.4040000",
     "errorMessage" : "Inventory does not exists",
     "id" : [ ]
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
| 200         | OK: The request is successful.                                                                                                                                                                      |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 400         | Bad Request: The request is invalid. The client should not repeat the request without modifications.                                                                                                |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 401         | Unauthorized: The authentication information is incorrect or invalid.                                                                                                                               |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 403         | Forbidden: The request is rejected. The server has received the request and understood it, but the server refuses to respond to it. The client should not repeat the request without modifications. |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 404         | Not Found: The requested resource could not be found. The client should not repeat this request without modification.                                                                               |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 500         | Internal Server Error: The server is able to receive the request but unable to understand the request.                                                                                              |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 503         | Unauthorized: The authentication information is incorrect or invalid.                                                                                                                               |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
