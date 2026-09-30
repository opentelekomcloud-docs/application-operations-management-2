:original_name: ListSeries.html

.. _ListSeries:

Querying Time Series Objects
============================

Function
--------

This API is used to query the time series objects that can be monitored in the system. You can specify a namespace, name, dimension, and resource ID (format: resType_resId). You can also specify the start position and the maximum number of returned records for a pagination query.

Calling Method
--------------

For details, see :ref:`Calling APIs <aom_04_0057>`.

URI
---

POST /v2/{project_id}/series

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+-------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                   |
   +============+===========+========+===============================================================================+
   | project_id | Yes       | String | Project ID obtained from IAM. Generally, a project ID contains 32 characters. |
   +------------+-----------+--------+-------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   +-----------+-----------+--------+-------------------------------------------------------------------------------+
   | Parameter | Mandatory | Type   | Description                                                                   |
   +===========+===========+========+===============================================================================+
   | limit     | No        | String | Maximum number of returned records. Value range: 1-1000. Default value: 1000. |
   +-----------+-----------+--------+-------------------------------------------------------------------------------+
   | offset    | No        | String | Start position of a pagination query. The value is a non-negative integer.    |
   +-----------+-----------+--------+-------------------------------------------------------------------------------+

Request Parameters
------------------

.. table:: **Table 3** Request body parameters

   +-----------+-----------+---------------------------------------------------------------------------------------------+-----------------------------------------+
   | Parameter | Mandatory | Type                                                                                        | Description                             |
   +===========+===========+=============================================================================================+=========================================+
   | series    | Yes       | Array of :ref:`QuerySeriesOptionParam <listseries__request_queryseriesoptionparam>` objects | Array for querying time series objects. |
   +-----------+-----------+---------------------------------------------------------------------------------------------+-----------------------------------------+

.. _listseries__request_queryseriesoptionparam:

.. table:: **Table 4** QuerySeriesOptionParam

   +-------------+-----------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter   | Mandatory | Type                                                                          | Description                                                                                                                                                                                                                                                                                                                                                                                   |
   +=============+===========+===============================================================================+===============================================================================================================================================================================================================================================================================================================================================================================================+
   | namespace   | Yes       | String                                                                        | Namespace of time series objects. Value range: PAAS.CONTAINER, PAAS.NODE, PAAS.SLA, PAAS.AGGR, or CUSTOMMETRICS. PAAS.CONTAINER: namespace of application time series objects. PAAS.NODE: namespace of node time series objects. PAAS.SLA: namespace of SLA time series objects. PAAS.AGGR: namespace of cluster time series objects. CUSTOMMETRICS: namespace of custom time series objects. |
   +-------------+-----------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | metric_name | No        | String                                                                        | Time series name. Length: 1 to 255 characters. Values: cpuUsage: CPU usage. cpuCoreUsed: used CPU cores. Custom time series names.                                                                                                                                                                                                                                                            |
   +-------------+-----------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | dimensions  | No        | Array of :ref:`DimensionSeries <listseries__request_dimensionseries>` objects | List of time series dimensions. You can call the /v2/{project_id}/series API to query the time series dimension list by namespace and metric_name.                                                                                                                                                                                                                                            |
   +-------------+-----------+-------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listseries__request_dimensionseries:

.. table:: **Table 5** DimensionSeries

   ========= ========= ====== ================
   Parameter Mandatory Type   Description
   ========= ========= ====== ================
   name      No        String Dimension name.
   value     No        String Dimension value.
   ========= ========= ====== ================

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 6** Response body parameters

   +-----------+--------------------------------------------------------------------------------------------+---------------------------------------------+
   | Parameter | Type                                                                                       | Description                                 |
   +===========+============================================================================================+=============================================+
   | series    | Array of :ref:`SeriesQueryItemResult <listseries__response_seriesqueryitemresult>` objects | List of time series objects.                |
   +-----------+--------------------------------------------------------------------------------------------+---------------------------------------------+
   | meta_data | :ref:`MetaDataSeries <listseries__response_metadataseries>` object                         | Metadata, including pagination information. |
   +-----------+--------------------------------------------------------------------------------------------+---------------------------------------------+

.. _listseries__response_seriesqueryitemresult:

.. table:: **Table 7** SeriesQueryItemResult

   +----------------------+--------------------------------------------------------------------------------+-------------------------+
   | Parameter            | Type                                                                           | Description             |
   +======================+================================================================================+=========================+
   | namespace            | String                                                                         | Namespace.              |
   +----------------------+--------------------------------------------------------------------------------+-------------------------+
   | dimensions           | Array of :ref:`DimensionSeries <listseries__response_dimensionseries>` objects | Dimension list.         |
   +----------------------+--------------------------------------------------------------------------------+-------------------------+
   | metric_name          | String                                                                         | Time series name.       |
   +----------------------+--------------------------------------------------------------------------------+-------------------------+
   | unit                 | String                                                                         | Time series unit.       |
   +----------------------+--------------------------------------------------------------------------------+-------------------------+
   | dimension_value_hash | String                                                                         | Time series hash value. |
   +----------------------+--------------------------------------------------------------------------------+-------------------------+

.. _listseries__response_dimensionseries:

.. table:: **Table 8** DimensionSeries

   ========= ====== ================
   Parameter Type   Description
   ========= ====== ================
   name      String Dimension name.
   value     String Dimension value.
   ========= ====== ================

.. _listseries__response_metadataseries:

.. table:: **Table 9** MetaDataSeries

   +-----------+---------+---------------------------------------------------------------------------+
   | Parameter | Type    | Description                                                               |
   +===========+=========+===========================================================================+
   | count     | Integer | Number of returned records.                                               |
   +-----------+---------+---------------------------------------------------------------------------+
   | offset    | Integer | Start of the next page, which is used for pagination. null: No more data. |
   +-----------+---------+---------------------------------------------------------------------------+
   | total     | Integer | Total number of records.                                                  |
   +-----------+---------+---------------------------------------------------------------------------+
   | nextToken | Integer | Offset.                                                                   |
   +-----------+---------+---------------------------------------------------------------------------+

**Status code: 400**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   error_type String Error type.
   ========== ====== ==============

Example Requests
----------------

Query time series objects by namespace and metric_name.

.. code-block::

   https://{Endpoint}/v2/{project_id}/series

   {
     "series" : [ {
       "namespace" : "PAAS.CONTAINER",
       "metric_name" : "aom_process_cpu_usage"
     } ]
   }

Example Responses
-----------------

**Status code: 200**

OK: The request is successful.

.. code-block::

   {
     "meta_data" : {
       "count" : 1,
       "offset" : null,
       "total" : 1,
       "nextToken" : 0
     },
     "series" : [ {
       "namespace" : "PAAS.CONTAINER",
       "metric_name" : "cpuUsage",
       "unit" : "Percent",
       "dimensions" : [ {
         "name" : "appName",
         "value" : "appValue"
       } ],
     "dimension_value_hash" : null
     } ]
   }

**Status code: 400**

Bad Request: The request is invalid. The client should not repeat the request without modifications.

.. code-block::

   {
     "error_code" : "AOM.04007001",
     "error_msg" : "please check request param",
     "error_type" : "BAD_REQUEST"
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
