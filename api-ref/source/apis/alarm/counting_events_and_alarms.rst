:original_name: CountEvents.html

.. _CountEvents:

Counting Events and Alarms
==========================

Function
--------

This API is used to count events and alarms that meet specified conditions.

Calling Method
--------------

For details, see :ref:`Calling APIs <aom_04_0057>`.

URI
---

POST /v2/{project_id}/events/statistic

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                   |
   +============+===========+========+===============================================================================+
   | project_id | Yes       | String | Project ID obtained from IAM. Generally, a project ID contains 32 characters. |
   +------------+-----------+--------+-------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                        |
   +=================+=================+=================+====================================================================================================================================================================================================================================================================================+
   | type            | No              | String          | Type of information to be queried. active_alert: Active alarms are to be queried. history_alert: Historical alarms are to be queried. If this parameter is not transferred or other values are transferred, information that meets the specified search criteria will be returned. |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | Enumeration values:                                                                                                                                                                                                                                                                |
   |                 |                 |                 |                                                                                                                                                                                                                                                                                    |
   |                 |                 |                 | -  **history_alert**                                                                                                                                                                                                                                                               |
   |                 |                 |                 | -  **active_alert**                                                                                                                                                                                                                                                                |
   +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

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

.. table:: **Table 4** Request body parameters

   +-------------------+-----------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter         | Mandatory       | Type                                                                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   +===================+=================+============================================================================+===============================================================================================================================================================================================================================================================================================================================================================================================================================================================+
   | time_range        | Yes             | String                                                                     | Time range specified to query data of the last N minutes when the client time is inconsistent with the server time. It can also be used to accurately query the data of a specified period.                                                                                                                                                                                                                                                                   |
   |                   |                 |                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                   |                 |                                                                            | Example:                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
   |                   |                 |                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                   |                 |                                                                            | -  -1.-1.60: indicates that the data of the latest 60 minutes is queried. This query is based on the server time regardless of the current client time.                                                                                                                                                                                                                                                                                                       |
   |                   |                 |                                                                            | -  1650852000000.1650852300000.5: indicates the five minutes from 10:00:00 to 10:05:00 on April 25, 2022 GMT+08:00.                                                                                                                                                                                                                                                                                                                                           |
   |                   |                 |                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                   |                 |                                                                            | Format:                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
   |                   |                 |                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                   |                 |                                                                            | startTimeInMillis.endTimeInMillis.durationInMinutes                                                                                                                                                                                                                                                                                                                                                                                                           |
   |                   |                 |                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                   |                 |                                                                            | Parameter description:                                                                                                                                                                                                                                                                                                                                                                                                                                        |
   |                   |                 |                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                   |                 |                                                                            | -  startTimeInMillis: Start time of the query, in milliseconds. If this parameter is set to -1, the server calculates the start time as follows: endTimeInMillis - durationInMinutes x 60 x 1000. For example, -1.1650852300000.5 is equivalent to 1650852000000.1650852300000.5.                                                                                                                                                                             |
   |                   |                 |                                                                            | -  endTimeInMillis: End time of the query, in milliseconds. If this parameter is set to -1, the server calculates the end time as follows: startTimeInMillis + durationInMinutes x 60 x 1000. If the calculated end time is later than the current system time, the current system time is used. For example, 1650852000000.-1.5 is equivalent to 1650852000000.1650852300000.5.                                                                              |
   |                   |                 |                                                                            | -  durationInMinutes: Time span, in minutes. The value must be greater than 0 and greater than or equal to the result of "(endTimeInMillis - startTimeInMillis)/(60 x 1000) - 1". If both the start time and end time are set to -1, the system sets the end time to the current UTC time (in milliseconds) and calculates the start time as follows: endTimeInMillis - durationInMinutes x 60 x 1000. For example, -1.-1.60 indicates the latest 60 minutes. |
   |                   |                 |                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                   |                 |                                                                            | Constraint:                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
   |                   |                 |                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
   |                   |                 |                                                                            | In a single request, the following condition must be met: durationInMinutes x 60/period <= 1440                                                                                                                                                                                                                                                                                                                                                               |
   +-------------------+-----------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | step              | Yes             | Long                                                                       | Statistical step (unit: ms). For example, if the statistical step is one minute, set this parameter to 60,000.                                                                                                                                                                                                                                                                                                                                                |
   +-------------------+-----------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | search            | No              | String                                                                     | Field specified for fuzzy query, which can be left blank. If this field is not left blank, the system will return metadata's mandatory fields that are fuzzily matched.                                                                                                                                                                                                                                                                                       |
   +-------------------+-----------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | sort              | No              | :ref:`sort <countevents__request_sort>` object                             | Sorting order, which can be left blank.                                                                                                                                                                                                                                                                                                                                                                                                                       |
   +-------------------+-----------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metadata_relation | No              | Array of :ref:`RelationModel <countevents__request_relationmodel>` objects | Combination of search criteria, which can be left blank.                                                                                                                                                                                                                                                                                                                                                                                                      |
   +-------------------+-----------------+----------------------------------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _countevents__request_sort:

.. table:: **Table 5** sort

   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                         |
   +=================+=================+==================+=====================================================================================+
   | order_by        | No              | Array of strings | List of sorted fields. Fields in this list are sorted based on the specified order. |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------+
   | order           | No              | String           | Sorting order. asc: ascending order. desc: descending order.                        |
   |                 |                 |                  |                                                                                     |
   |                 |                 |                  | Enumeration values:                                                                 |
   |                 |                 |                  |                                                                                     |
   |                 |                 |                  | -  **asc**                                                                          |
   |                 |                 |                  | -  **desc**                                                                         |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------+

.. _countevents__request_relationmodel:

.. table:: **Table 6** RelationModel

   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type             | Description                                                                                                                                                 |
   +=================+=================+==================+=============================================================================================================================================================+
   | key             | No              | String           | Key specified for query, which corresponds to the key in the metadata.                                                                                      |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | value           | No              | Array of strings | Value of the specified key in the search criterion.                                                                                                         |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | relation        | No              | String           | Relationship between search criteria. Values: AND: All criteria must be met. OR: One of the criteria needs to be met. NOT: None of the criteria can be met. |
   |                 |                 |                  |                                                                                                                                                             |
   |                 |                 |                  | Enumeration values:                                                                                                                                         |
   |                 |                 |                  |                                                                                                                                                             |
   |                 |                 |                  | -  **AND**                                                                                                                                                  |
   |                 |                 |                  | -  **OR**                                                                                                                                                   |
   |                 |                 |                  | -  **NOT**                                                                                                                                                  |
   +-----------------+-----------------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 7** Response body parameters

   +------------+-------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | Parameter  | Type                                                                    | Description                                                                                                    |
   +============+=========================================================================+================================================================================================================+
   | step       | Long                                                                    | Statistical step (unit: ms). For example, if the statistical step is one minute, set this parameter to 60,000. |
   +------------+-------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | timestamps | Array of longs                                                          | Time series object corresponding to the statistical result.                                                    |
   +------------+-------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+
   | series     | Array of :ref:`EventSeries <countevents__response_eventseries>` objects | Statistical results of a time series object's different severities of events or alarms.                        |
   +------------+-------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------+

.. _countevents__response_eventseries:

.. table:: **Table 8** EventSeries

   +-----------------------+-----------------------+-------------------------------------------------+
   | Parameter             | Type                  | Description                                     |
   +=======================+=======================+=================================================+
   | event_severity        | String                | Enumerated values of event or alarm severities. |
   |                       |                       |                                                 |
   |                       |                       | Enumeration values:                             |
   |                       |                       |                                                 |
   |                       |                       | -  **Critical**                                 |
   |                       |                       | -  **Major**                                    |
   |                       |                       | -  **Minor**                                    |
   |                       |                       | -  **Info**                                     |
   +-----------------------+-----------------------+-------------------------------------------------+
   | values                | Array of integers     | Event or alarm statistical result.              |
   +-----------------------+-----------------------+-------------------------------------------------+

**Status code: 400**

.. table:: **Table 9** Response body parameters

   ========== ====== ======================
   Parameter  Type   Description
   ========== ====== ======================
   error_code String Response code.
   error_msg  String Error description.
   error_type String API call failure type.
   ========== ====== ======================

**Status code: 401**

.. table:: **Table 10** Response body parameters

   ========== ====== ======================
   Parameter  Type   Description
   ========== ====== ======================
   error_code String Response code.
   error_msg  String Error description.
   error_type String API call failure type.
   ========== ====== ======================

**Status code: 403**

.. table:: **Table 11** Response body parameters

   ========== ====== ======================
   Parameter  Type   Description
   ========== ====== ======================
   error_code String Response code.
   error_msg  String Error description.
   error_type String API call failure type.
   ========== ====== ======================

**Status code: 500**

.. table:: **Table 12** Response body parameters

   ========== ====== ======================
   Parameter  Type   Description
   ========== ====== ======================
   error_code String Response code.
   error_msg  String Error description.
   error_type String API call failure type.
   ========== ====== ======================

**Status code: 503**

.. table:: **Table 13** Response body parameters

   ========== ====== ======================
   Parameter  Type   Description
   ========== ====== ======================
   error_code String Response code.
   error_msg  String Error description.
   error_type String API call failure type.
   ========== ====== ======================

Example Requests
----------------

Query the events and alarms on the step basis in a specified time range.

.. code-block::

   https://{endpoint}/v2/{project_id}/events/statistic

   {
     "time_range" : "-1.-1.5",
     "step" : 60000
   }

Example Responses
-----------------

**Status code: 200**

OK: The request is successful.

.. code-block::

   {
     "series" : [ {
       "event_severity" : "Minor",
       "values" : [ 0, 0, 0, 0, 0, 0 ]
     }, {
       "event_severity" : "Info",
       "values" : [ 0, 0, 0, 0, 0, 0 ]
     } ],
     "step" : 60000,
     "timestamps" : [ 1642820700000, 1642820760000, 1642820820000, 1642820880000, 1642820940000, 1642821000000 ]
   }

**Status code: 400**

Bad Request: The request is invalid. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "AOM.0400",
     "error_message" : "param error",
     "error_type" : "SC_BAD_REQUEST"
   }

**Status code: 401**

Unauthorized: The authentication information is incorrect or invalid.

.. code-block::

   {
     "error_code" : "AOM.0401",
     "error_message" : "You don't have permission.",
     "error_type" : "SC_UNAUTHORIZED"
   }

**Status code: 403**

Forbidden: The request is rejected. The server has received the request and understood it, but the server refuses to respond to it. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "AOM.0403",
     "error_message" : "Forbidden.",
     "error_type" : "SC_FORBIDDEN"
   }

**Status code: 500**

Internal Server Error: The server is able to receive the request but unable to understand the request.

.. code-block::

   {
     "error_code" : "AOM.0500",
     "error_message" : "Internal Server Error",
     "error_type" : "SC_INTERNAL_SERVER_ERROR"
   }

**Status code: 503**

Service Unavailable: The requested service is invalid. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "AOM.0503",
     "error_message" : "Server unavailable",
     "error_type" : "SC_NOT_IMPLEMENTED"
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
| 500         | Internal Server Error: The server is able to receive the request but unable to understand the request.                                                                                              |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| 503         | Service Unavailable: The requested service is invalid. The client should not repeat the request without modifications.                                                                              |
+-------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Error Codes
-----------

See :ref:`Error Codes <errorcode>`.
