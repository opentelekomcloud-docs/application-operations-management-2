:original_name: ListLogItems.html

.. _ListLogItems:

Querying Logs
=============

Function
--------

This API is used to query logs by different dimensions, such as by cluster, IP address, or application. Pagination queries are supported.

Calling Method
--------------

For details, see :ref:`Calling APIs <aom_04_0057>`.

URI
---

POST /v2/{project_id}/als/action

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                   |
   +============+===========+========+===============================================================================+
   | project_id | Yes       | String | Project ID obtained from IAM. Generally, a project ID contains 32 characters. |
   +------------+-----------+--------+-------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+--------+---------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                     |
   +===========+===========+========+=================================================================================+
   | type      | Yes       | String | Log API call mode. When the value is querylogs, this API is used to query logs. |
   +-----------+-----------+--------+---------------------------------------------------------------------------------+

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

   +-----------------+-----------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type                                                      | Description                                                                                                                                                                                                                          |
   +=================+=================+===========================================================+======================================================================================================================================================================================================================================+
   | category        | Yes             | String                                                    | Log type. Values: app_log: application log. node_log: node log.custom_log: log in a custom path.                                                                                                                                     |
   +-----------------+-----------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | endTime         | Yes             | Long                                                      | End time of the query (UTC, in ms).                                                                                                                                                                                                  |
   +-----------------+-----------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | hideSyslog      | No              | Integer                                                   | Whether to hide system logs during log queries. 0: Hide system logs. 1: Show system logs.                                                                                                                                            |
   +-----------------+-----------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | keyWord         | No              | String                                                    | Keyword for search.                                                                                                                                                                                                                  |
   |                 |                 |                                                           |                                                                                                                                                                                                                                      |
   |                 |                 |                                                           | #. Exact search by keyword is supported. A keyword is between two adjacent delimiters.                                                                                                                                               |
   |                 |                 |                                                           | #. Fuzzy search by keyword is supported. Example: RROR, ERRO?, *ROR*, ERR*, or ER*OR.                                                                                                                                                |
   |                 |                 |                                                           | #. Exact search by phrase is supported. Example: Start to refresh alm Statistic.                                                                                                                                                     |
   |                 |                 |                                                           | #. Search using AND (&&) or OR (||) is supported. Example: query&&logs or query||logs. Note: Default delimiters: , ``'";=()[]{}@&<>/:\``\ n\\t\\r                                                                                    |
   +-----------------+-----------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | lineNum         | No              | String                                                    | Sequence number of the final log in the last query result. This parameter is not required for the first query, but is required for subsequent pagination queries.                                                                    |
   +-----------------+-----------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | pageSize/size   | No              | String                                                    | Number of logs queried each time. Default value: 5000. Recommended value: 100. For the first query, pageSize is used. For subsequent pagination queries, size is used.                                                               |
   +-----------------+-----------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | searchKey       | Yes             | :ref:`SearchKey <listlogitems__request_searchkey>` object | Log filter criteria, which vary according to log sources.                                                                                                                                                                            |
   +-----------------+-----------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | startTime       | Yes             | Long                                                      | Start time of the query (UTC, in ms).                                                                                                                                                                                                |
   +-----------------+-----------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | type            | No              | String                                                    | Pagination query. This parameter is not required for the first query, but is required for subsequent pagination queries.                                                                                                             |
   +-----------------+-----------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | isDesc          | No              | Boolean                                                   | Whether to query logs based on lineNum in ascending or descending order. true: lineNum in descending order (from the latest time to the earliest time) false: lineNum in ascending order (from the earliest time to the latest time) |
   +-----------------+-----------------+-----------------------------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listlogitems__request_searchkey:

.. table:: **Table 5** SearchKey

   ========= ========= ====== ============================================
   Parameter Mandatory Type   Description
   ========= ========= ====== ============================================
   appName   No        String Application name.
   clusterId Yes       String CCE cluster ID.
   hostIP    No        String IP address of the VM where logs are located.
   nameSpace No        String CCE cluster namespace.
   pathFile  No        String Log file name.
   podName   No        String Container instance name.
   ========= ========= ====== ============================================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 6** Response body parameters

   +--------------+--------+-----------------------------------------------------------------------+
   | Parameter    | Type   | Description                                                           |
   +==============+========+=======================================================================+
   | errorCode    | String | Response code. SVCSTG_AMS_2000000: Success response.                  |
   +--------------+--------+-----------------------------------------------------------------------+
   | errorMessage | String | Response message.                                                     |
   +--------------+--------+-----------------------------------------------------------------------+
   | result       | String | Metadata, including results and the total number of returned records. |
   +--------------+--------+-----------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 7** Response body parameters

   ============ ====== =================
   Parameter    Type   Description
   ============ ====== =================
   errorCode    String Response code.
   errorMessage String Response message.
   ============ ====== =================

**Status code: 401**

.. table:: **Table 8** Response body parameters

   ============ ====== =================
   Parameter    Type   Description
   ============ ====== =================
   errorCode    String Response code.
   errorMessage String Response message.
   ============ ====== =================

**Status code: 403**

.. table:: **Table 9** Response body parameters

   ============ ====== =================
   Parameter    Type   Description
   ============ ====== =================
   errorCode    String Response code.
   errorMessage String Response message.
   ============ ====== =================

**Status code: 500**

.. table:: **Table 10** Response body parameters

   ============ ====== =================
   Parameter    Type   Description
   ============ ====== =================
   errorCode    String Response code.
   errorMessage String Response message.
   ============ ====== =================

**Status code: 503**

.. table:: **Table 11** Response body parameters

   ============ ====== =================
   Parameter    Type   Description
   ============ ====== =================
   errorCode    String Response code.
   errorMessage String Response message.
   ============ ====== =================

Example Requests
----------------

-  Example 1: Query application logs under a cluster.

   .. code-block:: text

      POST https://{endpoint}/v2/{project_id}/als/action?type=querylogs

      {
        "category" : "app_log",
        "endTime" : 15389000003,
        "hideSyslog" : 0,
        "keyWord" : "",
        "searchKey" : {
          "clusterId" : "c69xxxc-5xxx-1xxx-8xxx5-02xxxxx40"
        },
        "startTime" : 15389000003
      }

-  Example 2: Perform pagination queries. Notes:

   #. For pagination queries, the lineNum (sequence number of the final log in the last query result), type (value: next), and size parameters need to be added.
   #. The values of category, searchKey, keyWord, startTime, and endTime must be the same as those in the first query.
   #. To implement another pagination query, change the value of lineNum to the sequence number of the final log in the last query result. The rest may be deduced by analogy.

   .. code-block:: text

      POST https://{endpoint}/v2/{project_id}/als/action?type=querylogs

      {
        "category" : "app_log",
        "searchKey" : {
          "clusterId" : "874xxx9a2-xxxf-xxx-8xxe-02xxxxx3"
        },
        "keyWord" : "",
        "startTime" : 156946300095,
        "endTime" : 15694600008895,
        "lineNum" : "1569463900000047",
        "type" : "next",
        "size" : 100,
        "hideSyslog" : 0
      }

Example Responses
-----------------

**Status code: 200**

OK: The request is successful.

.. code-block::

   {
     "errorCode" : "SVCSTG.ALS.200.200",
     "errorMessage" : "Query data success",
     "result" : [ {
       "data" : [ {
         "appName" : "axxs0712",
         "category" : "apx",
         "clusterId" : "c6xxxx7c-54cd-11e8-8055-025xxx1e40",
         "collectTime" : 153900000983,
         "time" : 153900000983,
         "containerName" : "contsssner-0",
         "hostIP" : "1xx.xxx.0.1xxx",
         "hostId" : "c11xxxxx11-0000b-4925-bef4-d0xxxx9b0",
         "hostName" : "1x2.168.0.xxx",
         "lineNum" : "1xxx23xxxxxx2VW5xxxxxx0ZWdlcg==",
         "logContent" : "warn:2018/10/09 06:57:01 helloworld.go:108: the main processis running now.",
         "logContentSize" : null,
         "loghash" : "4xxxxx0d40a83c17f262540xxxxxxxxfeaa30eb",
         "nameSpace" : "default",
         "pathFile" : "/xxx/xxx/xxx/xxx/xxx/xxx.trxe",
         "podName" : "axxx12-7xxf884-qxxwp",
         "serviceID" : ""
       } ],
       "total" : 5000
     } ]
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
