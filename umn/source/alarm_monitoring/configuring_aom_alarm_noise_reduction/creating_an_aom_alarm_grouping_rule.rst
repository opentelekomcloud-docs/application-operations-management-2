:original_name: mon_01_0019.html

.. _mon_01_0019:

Creating an AOM Alarm Grouping Rule
===================================

After you create alarm grouping rules, AOM filters alarm subsets and then groups them based on grouping conditions.

Constraints
-----------

-  You can create a maximum of 100 grouping rules. If this number has been reached, delete unnecessary rules.

Procedure
---------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Alarm Center** > **Alarm Noise Reduction**.

#. On the **Grouping Rules** tab page, click **Create** and set parameters such as the rule name and grouping condition. For details, see :ref:`Table 1 <mon_01_0019__table169384396812>`.

   .. _mon_01_0019__table169384396812:

   .. table:: **Table 1** Grouping rule parameters

      +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Category              | Parameter                 | Description                                                                                                                                                                                                                                                                |
      +=======================+===========================+============================================================================================================================================================================================================================================================================+
      | ``-``                 | Rule Name                 | Name of a grouping rule.                                                                                                                                                                                                                                                   |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | Enter up to 100 characters and do not start or end with an underscore (_). Only letters, digits, and underscores are allowed.                                                                                                                                              |
      +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Enterprise Project        | Enterprise project.                                                                                                                                                                                                                                                        |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | -  If you have selected **All** for **Enterprise Project** on the global settings page, select one from the drop-down list here.                                                                                                                                           |
      |                       |                           | -  If you have already selected an enterprise project on the global settings page, this option will be dimmed and cannot be changed.                                                                                                                                       |
      +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Description               | Description of a grouping rule. Enter up to 1,024 characters.                                                                                                                                                                                                              |
      +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Grouping Rule         | Grouping Condition        | Conditions set to filter alarms. After alarms are filtered out, you can set notification rules for them.                                                                                                                                                                   |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | Value range and description:                                                                                                                                                                                                                                               |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | -  **Alarm Severity**: severity of a metric or event alarm. Options: **Critical**, **Major**, **Minor**, and **Warning**. Example: **Alarm Severity** + **Equals To** + **Critical**                                                                                       |
      |                       |                           | -  **Resource Type**: resource type selected when you create an alarm rule or customize alarm reporting. Options: include **host**, **container**, and **process**. Example: **Resource Type** + **Equals To** + **container**                                             |
      |                       |                           | -  **Alarm Source**: name of the service that triggers the alarm or event. Options: include **AOM**, **LTS**, and **CCE**. Example: **Alarm Source** + **Equals To** + **AOM**                                                                                             |
      |                       |                           | -  **Tag**: alarm identification attribute, which consists of the tag name and tag value and can be customized. Example: **Tag** + **aom_monitor_level** + **Equals To** + **infrastructure**                                                                              |
      |                       |                           | -  **Notify When**: scenario when notifications are triggered. Options: **Alarm triggered** and **Alarm cleared**. Example: **Notify When** + **Alarm triggered**.                                                                                                         |
      |                       |                           | -  *XX* + **Exists**: indicates the alarm whose metadata contains *XX*. Example: For **Alarm Source** + **Exists**, the alarms whose metadata contains the alarm source will be filtered.                                                                                  |
      |                       |                           | -  *XX* + **Regular Expression**: indicates the alarm whose *XX* matches the regular expression. Example: For **Resource Type** + **Regular Expression** + **host\***, the alarms whose resource type contains **host** will be filtered.                                  |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | Rule description:                                                                                                                                                                                                                                                          |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | -  You can create a maximum of 10 parallel conditions, each of which can contain up to 10 serial conditions. One or more :ref:`AOM alarm notification rules <mon_01_0013>` can be set for each parallel condition.                                                         |
      |                       |                           | -  Serial conditions are in the AND relationship whereas parallel conditions are in the OR relationship. An alarm must meet all serial conditions under one of the parallel conditions.                                                                                    |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | For example, if two serial conditions (that is, **Alarm Severity** = **Critical** and **Alarm Source** = **AOM**) are set under a parallel condition, critical AOM alarms are filtered out, and notification actions are performed based on the notification rule you set. |
      +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Combination Rule      | Combine Notifications     | Combines grouped alarms based on specified fields. Alarms in the same group are aggregated for sending one notification.                                                                                                                                                   |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | Notifications can be combined:                                                                                                                                                                                                                                             |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | -  **By alarm source**: Alarms triggered by the same alarm source are combined into one group for sending notifications.                                                                                                                                                   |
      |                       |                           | -  **By alarm source + severity**: Alarms triggered by the same alarm source and of the same severity are combined into one group for sending notifications.                                                                                                               |
      |                       |                           | -  **By alarm source + all tags**: Alarms triggered by the same alarm source and with the same tag are combined into one group for sending notifications.                                                                                                                  |
      +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Initial Wait Time         | Interval for sending an alarm notification after alarms are combined for the first time. It is recommended that the time be set to seconds to prevent alarm storms.                                                                                                        |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | Value range: 0s to 10 minutes. Recommended: 15s.                                                                                                                                                                                                                           |
      +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Batch Processing Interval | Waiting time for sending an alarm notification after the combined alarm data changes. It is recommended that the time be set to minutes. If you want to receive alarm notifications as soon as possible, set the time to seconds.                                          |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | The change here refers to a new alarm or an alarm status change.                                                                                                                                                                                                           |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | Value range: 5s to 30 minutes. Recommended: 60s.                                                                                                                                                                                                                           |
      +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Repeat Interval           | Waiting time for sending an alarm notification after the combined alarm data becomes duplicate. It is recommended that the time be set to hours.                                                                                                                           |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | Duplication means that no new alarm is generated and no alarm status is changed while other attributes (such as titles and content) are changed.                                                                                                                           |
      |                       |                           |                                                                                                                                                                                                                                                                            |
      |                       |                           | Value range: 0 minutes to 15 days. Recommended: 1 hour.                                                                                                                                                                                                                    |
      +-----------------------+---------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Confirm**.

More Operations
---------------

After creating a grouping rule, perform the operations listed in :ref:`Table 2 <mon_01_0019__en-us_topic_0169698264_table14918185010104>` if needed.

.. _mon_01_0019__en-us_topic_0169698264_table14918185010104:

.. table:: **Table 2** Related operations

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------+
   | Operation                         | Description                                                                                                 |
   +===================================+=============================================================================================================+
   | Checking a grouping rule          | Click the name of a grouping rule in the rule list to view its details.                                     |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------+
   | Modifying a grouping rule         | Click **Modify** in the **Operation** column.                                                               |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------+
   | Deleting a grouping rule          | -  To delete a single rule, click **Delete** in the **Operation** column in the row that contains the rule. |
   |                                   | -  To delete one or more rules, select them and click **Delete** above the rule list.                       |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------+
   | Searching for a grouping rule     | Enter a rule name in the search box in the upper right corner and click |image1|.                           |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002371030197.png
