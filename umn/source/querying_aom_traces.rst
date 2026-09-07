:original_name: mon_01_0064.html

.. _mon_01_0064:

Querying AOM Traces
===================

AOM is a one-stop O&M platform that monitors applications and resources in real time. By analyzing dozens of metrics and correlation between alarms and logs, AOM helps O&M personnel quickly locate faults.

You can use AOM to comprehensively monitor and uniformly manage servers, storage, networks, web containers, and applications hosted in Docker and Kubernetes. This effectively prevents problems and helps O&M personnel locate faults in minutes, reducing O&M costs. Also, AOM provides unified APIs to interconnect in-house monitoring or report systems. Unlike traditional monitoring systems, AOM monitors services by application. It meets enterprises' requirements for high efficiency and fast iteration, provides effective IT support for their services, and protects and optimizes their IT assets, enabling enterprises to achieve strategic goals and maximize value. With CTS, you can record operations associated with AOM for future query, audit, and backtracking.

Enabling CTS
------------

Before using CTS, enable it.

After CTS is enabled, if you want to view AOM traces, see "Querying Real-Time Traces" in the *Cloud Trace Service User Guide*.

AOM Operations That Can Be Recorded by CTS
------------------------------------------

**pe** traces actually record AOM operations, but these operations are performed through CCE.

.. table:: **Table 1** Operations logged by CTS

   +----------------------+--------------------------------------+----------------------+-------------------------+
   | Function             | Operation                            | Resource Type        | Trace                   |
   +======================+======================================+======================+=========================+
   | Global configuration | Adding an access code                | icmgr                | icmgrAddAccessCode      |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Deleting an access code              | icmgr                | icmgrDelAccessCode      |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   | Resource monitoring  | Creating a dashboard                 | dashboard            | updateDashboard         |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Deleting a dashboard                 | dashboard            | deleteDashboard         |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Updating a dashboard                 | dashboard            | updateDashboard         |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Creating a dashboard group           | dashboard_folder     | addDashboardFolder      |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Updating a dashboard group           | dashboard_folder     | updateDashboardFolder   |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Deleting a dashboard group           | dashboard_folder     | deleteDashboardFolder   |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Creating an alarm rule               | audit_v4_alarm_rule  | addAlarm                |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Updating an alarm rule               | audit_v4_alarm_rule  | updateAlarm             |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Deleting an alarm rule               | audit_v4_alarm_rule  | DeleteThresholdRule     |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Creating a process discovery rule    | apminventory         | addOrUpdateAppRules     |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Updating a process discovery rule    | apminventory         | addOrUpdateAppRules     |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Deleting a process discovery rule    | apminventory         | deleteAppRules          |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Adding an alarm template             | audit_v4_alarm_rule  | addAlarmRuleTemplate    |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Modifying an alarm template          | audit_v4_alarm_rule  | modifyAlarmRuleTemplate |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Deleting an alarm template           | audit_v4_alarm_rule  | deleteAlarmRuleTemplate |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Adding a grouping rule               | groupRule            | addGroupRule            |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Modifying a grouping rule            | groupRule            | updateGroupRule         |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Deleting a grouping rule             | groupRule            | delGroupRule            |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Adding a suppression rule            | inhibitRule          | addInhibitRule          |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Modifying a suppression rule         | inhibitRule          | updateInhibitRule       |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Deleting a suppression rule          | inhibitRule          | delInhibitRule          |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Adding a silence rule                | muteRule             | addMuteRule             |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Modifying a silence rule             | muteRule             | updateMuteRule          |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Deleting a silence rule              | muteRule             | delMuteRule             |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Adding an alarm notification rule    | actionRule           | addActionRule           |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Modifying an alarm notification rule | actionRule           | updateActionRule        |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Deleting an alarm notification rule  | actionRule           | delActionRule           |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Adding a message template            | notificationTemplate | addNotificationTemplate |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Modifying a message template         | notificationTemplate | updateTemplate          |
   +----------------------+--------------------------------------+----------------------+-------------------------+
   |                      | Deleting a message template          | notificationTemplate | delTemplate             |
   +----------------------+--------------------------------------+----------------------+-------------------------+
