:original_name: ListNotifiedHistories.html

.. _ListNotifiedHistories:

Obtaining the Alarm Sending Result
==================================

Function
--------

This API is used to obtain the alarm sending result.

Calling Method
--------------

For details, see :ref:`Calling APIs <aom_04_0057>`.

URI
---

GET /v2/{project_id}/alarm-notified-histories

.. table:: **Table 1** Path Parameters

   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter  | Mandatory | Type   | Description                                                                                                                            |
   +============+===========+========+========================================================================================================================================+
   | project_id | Yes       | String | Project ID, which can be obtained from the console or by calling an API. For details, see :ref:`Obtaining a Project ID <aom_04_0024>`. |
   +------------+-----------+--------+----------------------------------------------------------------------------------------------------------------------------------------+

.. table:: **Table 2** Query Parameters

   ========= ========= ====== ====================
   Parameter Mandatory Type   Description
   ========= ========= ====== ====================
   event_sn  Yes       String Alarm serial number.
   ========= ========= ====== ====================

Request Parameters
------------------

.. table:: **Table 3** Request header parameters

   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | Parameter       | Mandatory       | Type            | Description                                                                            |
   +=================+=================+=================+========================================================================================+
   | X-Auth-Token    | Yes             | String          | User token obtained from IAM. For details, see :ref:`Obtaining a Token <aom_04_0059>`. |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+
   | Content-Type    | No              | String          | Message body type or format. Content type, which is application/json.                  |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | Enumeration values:                                                                    |
   |                 |                 |                 |                                                                                        |
   |                 |                 |                 | -  **application/json**                                                                |
   +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------+

Response Parameters
-------------------

**Status code: 200**

.. table:: **Table 4** Response body parameters

   +--------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+
   | Parameter          | Type                                                                                                                                   | Description                   |
   +====================+========================================================================================================================================+===============================+
   | notified_histories | Array of :ref:`NotifiedHistoriesResult <listnotifiedhistories__en-us_topic_0000001607551917_response_notifiedhistoriesresult>` objects | Historical notification list. |
   +--------------------+----------------------------------------------------------------------------------------------------------------------------------------+-------------------------------+

.. _listnotifiedhistories__en-us_topic_0000001607551917_response_notifiedhistoriesresult:

.. table:: **Table 5** NotifiedHistoriesResult

   +---------------+--------------------------------------------------------------------------------------------------------------------+----------------------+
   | Parameter     | Type                                                                                                               | Description          |
   +===============+====================================================================================================================+======================+
   | event_sn      | String                                                                                                             | Alarm SN.            |
   +---------------+--------------------------------------------------------------------------------------------------------------------+----------------------+
   | notifications | Array of :ref:`Notifications <listnotifiedhistories__en-us_topic_0000001607551917_response_notifications>` objects | Notification result. |
   +---------------+--------------------------------------------------------------------------------------------------------------------+----------------------+

.. _listnotifiedhistories__en-us_topic_0000001607551917_response_notifications:

.. table:: **Table 6** Notifications

   +-----------------------+------------------------------------------------------------------------------------------------------+----------------------------------------------------------+
   | Parameter             | Type                                                                                                 | Description                                              |
   +=======================+======================================================================================================+==========================================================+
   | action_rule           | String                                                                                               | Alarm notification rule name.                            |
   +-----------------------+------------------------------------------------------------------------------------------------------+----------------------------------------------------------+
   | notifier_channel      | String                                                                                               | Notification type. **SMN**: Simple Message Notification. |
   |                       |                                                                                                      |                                                          |
   |                       |                                                                                                      | Enumeration values:                                      |
   |                       |                                                                                                      |                                                          |
   |                       |                                                                                                      | -  **SMN**                                               |
   +-----------------------+------------------------------------------------------------------------------------------------------+----------------------------------------------------------+
   | smn_channel           | :ref:`SmnResponse <listnotifiedhistories__en-us_topic_0000001607551917_response_smnresponse>` object | Notification result details.                             |
   +-----------------------+------------------------------------------------------------------------------------------------------+----------------------------------------------------------+

.. _listnotifiedhistories__en-us_topic_0000001607551917_response_smnresponse:

.. table:: **Table 7** SmnResponse

   +----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Parameter            | Type                                                                                                   | Description                                                                                                                                    |
   +======================+========================================================================================================+================================================================================================================================================+
   | sent_time            | Long                                                                                                   | Sending time (UTC timestamp, in milliseconds). Example: 2024-10-16 16:03:01 needs to be converted to UTC timestamp 1702759381000 using a tool. |
   +----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | smn_notified_history | Array of :ref:`SmnInfo <listnotifiedhistories__en-us_topic_0000001607551917_response_smninfo>` objects | Content of a notification.                                                                                                                     |
   +----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | smn_request_id       | String                                                                                                 | ID for requesting SMN.                                                                                                                         |
   +----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | smn_response_body    | String                                                                                                 | Information returned after the SMN service is invoked.                                                                                         |
   +----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | smn_response_code    | String                                                                                                 | HTTP status code returned after the SMN service is invoked.                                                                                    |
   +----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | smn_topic            | String                                                                                                 | SMN topic.                                                                                                                                     |
   +----------------------+--------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

.. _listnotifiedhistories__en-us_topic_0000001607551917_response_smninfo:

.. table:: **Table 8** SmnInfo

   ======================= ======= ========================
   Parameter               Type    Description
   ======================= ======= ========================
   smn_notified_content    String  SMN message content.
   smn_subscription_status Integer SMN subscription status.
   smn_subscription_type   String  SMN subscription type.
   ======================= ======= ========================

**Status code: 401**

.. table:: **Table 9** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   error_type String Error type.
   trace_id   String Request ID.
   ========== ====== ==============

**Status code: 403**

.. table:: **Table 10** Response body parameters

   ========== ====== ==============
   Parameter  Type   Description
   ========== ====== ==============
   error_code String Error code.
   error_msg  String Error message.
   error_type String Error type.
   trace_id   String Request ID.
   ========== ====== ==============

**Status code: 500**

.. table:: **Table 11** Response body parameters

   ========== ====== =================
   Parameter  Type   Description
   ========== ====== =================
   error_code String Response code.
   error_msg  String Response message.
   trace_id   String Response ID.
   ========== ====== =================

Example Requests
----------------

Obtain the sending result of the alarm whose serial number is 1044686593798963201.

.. code-block::

   https://{Endpoint}/v2/{project_id}/alarm-notified-histories?event_sn=1044686593798963201

Example Responses
-----------------

**Status code: 200**

OK: The request is successful.

.. code-block::

   {
     "notified_histories" : [ {
       "event_sn" : "1044686593798963201",
       "notifications" : [ {
         "action_rule" : "lhy_alarm_action_test01",
         "notifier_channel" : "SMN",
         "smn_channel" : {
           "sent_time" : 1669114269797,
           "smn_notified_history" : [ {
             "smn_notified_content" : "<style>    span {        display: inline-block;        float: left;        font-size: 14px;    }    b {        display: inline-block;        float: left;        color: #252B3A;        font-size: 14px    }</style><table border=\"0\" cellpadding=\"0\" cellspacing=\"0\"       style=\"font-family:Helvetica,Arial,PingFangSC-Regular,Hiragino Sans GB;border-spacing:0px 14px;font-size:14px;padding-left: 30px;line-height:25px;\">    <thead>    <tr style=\"font-size:14px;\">        <td colspan=\"2\" style=\"line-height:28px;color:#6e6e6e;font-size:14px\">            <b>Dear&nbsp;</b>            <b>users</b>            <b>&nbsp;</b>        </td>    </tr>    </thead>    <tr>        <td colspan=\"2\">            <span>1 notification has been&nbsp;</span>            <b>generated</b>            <span>&nbsp;in region ***</span>            <b>&nbsp;based on action rule lhy_alarm_action_test01.</b>            <span></span>            <span></span>                                    <span><span>The alarm rule is&nbsp;</span><b>lhy_test_001</b></span>            <span>. For more information, go to the AOM console.</span>            <br>            <br>        </td>    </tr>    <tr style=\"font-size:14px;\">        <td colspan=\"2\">            <p style=\"margin-bottom: -20px; margin-top: -26px;\">                <span style=\"color:#252B3A;line-height:24px\">Here are the details.</span>            </p>        </td>    </tr>    <td><div>Account: kaifatest;<br>Notification Type: alarm;<br>CAS Application Name: app-1;<br>Notification Type: NA;<br>Severity: Critical;<br>Name: lhy_test_001;<br>Occurred: 2022-11-22 18:51:05 GMT+08:00;<br>Source: AOM;<br>Resource Type: Application;<br>Resource Identifier: <br>&nbsp;&nbsp;casApplicationID: 2d216a2b-9a58-452e-9a82-fc0c7cbcd322;<br>&nbsp;&nbsp;casApplicationName: app-1;<br>Possible Cause: If the specified metric value crosses the threshold and the alarm severity is \\\"critical\\\", an alarm is triggered.;<br>Link: https://console.xxx/aom/alarmlist;<br>Additional Info: The threshold rule lhy_test_001 status changes from \\\"init\\\" to \\\"alarm\\\". The value of \\\"cpuCoreLimit\\\" is \\\"0.250\\\" and meets the threshold criterion \\\">=0\\\"<br>Suggestion: NA;<br><div/></td>  </table>",
             "smn_subscription_status" : 1,
             "smn_subscription_type" : "email"
           }, {
             "smn_notified_content" : "[AOM][Critical_alarm_generated] \nAlert Name: lhy_test_001;\nCAS Application Name: app-1;\nOccurrence Time: 2022-11-22 18:51:05 GMT+08:00;\nLink: https://console.xxx/aom/alarmlist;\nAlert Content: The threshold rule lhy_test_001 status changes from \"init\" to \"alarm\". The value of \"cpuCoreLimit\" is \"0.250\" and meets the threshold criterion \">=0\".;\nThis message is configured in an AOM alarm rule by kaifatest. For more information, go to the AOM console.\",",
             "smn_subscription_status" : 0,
             "smn_subscription_type" : "sms"
           }, {
             "smn_notified_content" : "[AOM][Critical_alarm_generated] \nAlert Name: lhy_test_001;\nCAS Application Name: app-1;\nOccurrence Time: 2022-11-22 18:51:05 GMT+08:00;\nLink: https://console.xxx/aom/alarmlist;\nAlert Content: The threshold rule lhy_test_001 status changes from \"init\" to \"alarm\". The value of \"cpuCoreLimit\" is \"0.250\" and meets the threshold criterion \">=0\".;\nThis message is configured in an AOM alarm rule by kaifatest. For more information, go to the AOM console.\",",
             "smn_subscription_status" : 0,
             "smn_subscription_type" : "sms"
           } ],
           "smn_request_id" : "600bfa7447da48068312bba0fb2b3afa",
           "smn_response_body" : "{\"message_id\":\"b5db3a3419b84cc29d438a7dba336c20\",\"request_id\":\"600bfa7447da48068312bba0fb2b3afa\"}",
           "smn_response_code" : "200",
           "smn_topic" : "lhy_test01"
         }
       } ]
     } ]
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
| 200         | OK: The request is successful.                                                                                                                                                                      |
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
