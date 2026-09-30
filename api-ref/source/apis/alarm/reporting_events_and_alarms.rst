:original_name: PushEvents.html

.. _PushEvents:

Reporting Events and Alarms
===========================

Function
--------

This API is used to report events and alarms of a user.

Calling Method
--------------

For details, see :ref:`Calling APIs <aom_04_0057>`.

URI
---

PUT /v2/{project_id}/push/events

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                   |
   +============+===========+========+===============================================================================+
   | project_id | Yes       | String | Project ID obtained from IAM. Generally, a project ID contains 32 characters. |
   +------------+-----------+--------+-------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                  |
   +=================+=================+=================+==============================================================================================================================================================+
   | action          | No              | String          | Requested action. clear: The alarm is to be cleared. If this parameter is not transferred or other values are transferred, the alarm is reported by default. |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | Enumeration values:                                                                                                                                          |
   |                 |                 |                 |                                                                                                                                                              |
   |                 |                 |                 | -  **clear**                                                                                                                                                 |
   +-----------------+-----------------+-----------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-------------------------+-----------------+-----------------+----------------------------------------------------------+
   | Parameter               | Mandatory       | Type            | Description                                              |
   +=========================+=================+=================+==========================================================+
   | X-Auth-Token            | Yes             | String          | User token obtained from IAM.                            |
   +-------------------------+-----------------+-----------------+----------------------------------------------------------+
   | Content-Type            | Yes             | String          | Content type, which is application/json.                 |
   |                         |                 |                 |                                                          |
   |                         |                 |                 | Enumeration values:                                      |
   |                         |                 |                 |                                                          |
   |                         |                 |                 | -  **application/json**                                  |
   +-------------------------+-----------------+-----------------+----------------------------------------------------------+
   | x-enterprise-project-id | No              | String          | ID of the enterprise project to which the alarm belongs. |
   +-------------------------+-----------------+-----------------+----------------------------------------------------------+

.. table:: **Table 4** Request body parameters

   +-----------+-----------+---------------------------------------------------------------------+-------------------------+
   | Parameter | Mandatory | Type                                                                | Description             |
   +===========+===========+=====================================================================+=========================+
   | events    | Yes       | Array of :ref:`EventModel <pushevents__request_eventmodel>` objects | Event or alarm details. |
   +-----------+-----------+---------------------------------------------------------------------+-------------------------+

.. _pushevents__request_eventmodel:

.. table:: **Table 5** EventModel

   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type               | Description                                                                                                                                                                                                                                                                   |
   +=================+=================+====================+===============================================================================================================================================================================================================================================================================+
   | starts_at       | No              | Long               | Time when an event or alarm is generated (CST timestamp precise down to the millisecond).                                                                                                                                                                                     |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | ends_at         | No              | Long               | Time when an event or alarm is cleared (CST timestamp precise down to the millisecond). 0: The event or alarm is not deleted.                                                                                                                                                 |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | timeout         | No              | Long               | Duration (in milliseconds) at which an alarm is automatically cleared. For example, if an alarm needs to be automatically cleared in one minute, set this parameter to 60000. The default value is 3 days (that is, 3 days x 24 hours x 60 minutes x 1000 ms = 4,320,000 ms). |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata        | No              | Map<String,String> | Details of an event or alarm. The value is a key-value pair. The following fields are mandatory:                                                                                                                                                                              |
   |                 |                 |                    |                                                                                                                                                                                                                                                                               |
   |                 |                 |                    | -  **event_name**: event or alarm name, which is a string.                                                                                                                                                                                                                    |
   |                 |                 |                    | -  **event_severity**: event severity, which is an enumerated value with string elements. Options: **Critical**, **Major**, **Minor**, and **Info**.                                                                                                                          |
   |                 |                 |                    | -  **event_type**: event type, which is an enumerated value with string elements. Options: **event** and **alarm**.                                                                                                                                                           |
   |                 |                 |                    | -  **resource_provider**: name of a cloud service corresponding to an event, which is a string.                                                                                                                                                                               |
   |                 |                 |                    | -  **resource_type**: type of the resource corresponding to an event, which is a string.                                                                                                                                                                                      |
   |                 |                 |                    | -  **resource_id**: resource ID corresponding to an event, which is a string.                                                                                                                                                                                                 |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | annotations     | No              | Map<String,Object> | Additional field for an event or alarm, which can be left blank.                                                                                                                                                                                                              |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | attach_rule     | No              | Map<String,Object> | Reserved field for an event or alarm, which can be left blank.                                                                                                                                                                                                                |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | id              | No              | String             | Event or alarm ID, which is automatically generated by the system.                                                                                                                                                                                                            |
   +-----------------+-----------------+--------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 204**

No Content: The request is successful, but no content is returned.

**Status code: 400**

.. table:: **Table 6** Response body parameters

   ========== ====== ======================
   Parameter  Type   Description
   ========== ====== ======================
   error_code String Response code.
   error_msg  String Error description.
   error_type String API call failure type.
   trace_id   String Request ID.
   ========== ====== ======================

Example Requests
----------------

Report an alarm named "test".

.. code-block::

   https://{EndPoint}/v2/{project_id}/push/events

   {
     "events" : [ {
       "starts_at" : 1605232501000,
       "timeout" : 60000,
       "metadata" : {
         "event_name" : "test",
         "event_severity" : "Major",
         "event_type" : "alarm",
         "resource_provider" : "ecs",
         "resource_type" : "vm",
         "resource_id" : "ecs123"
       },
       "annotations" : {
         "alarm_probableCause_zh_cn" : "Possible Causes",
         "alarm_fix_suggestion_zh_cn" : "Suggestions",
         "message" : "Alarm Details"
       },
       "attach_rule" : { }
     } ]
   }

Example Responses
-----------------

**Status code: 400**

Bad Request: The request is invalid. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "AOM.0400",
     "error_msg" : "parse eventParam failed",
     "error_type" : "SC_BAD_REQUEST"
   }

Status Codes
------------

+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| Status Code | Description                                                                                                                                                                                         |
+=============+=====================================================================================================================================================================================================+
| 204         | No Content: The request is successful, but no content is returned.                                                                                                                                  |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 400         | Bad Request: The request is invalid. The client should not repeat the request without modifications.                                                                                                |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 401         | Unauthorized: The authentication information is incorrect or invalid.                                                                                                                               |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 403         | Forbidden: The request is rejected. The server has received the request and understood it, but the server refuses to respond to it. The client should not repeat the request without modifications. |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 500         | Internal Server Error: The server is able to receive the request but unable to understand the request.                                                                                              |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 503         | Service Unavailable: The requested service is invalid. The client should not repeat the request without modifications.                                                                              |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
