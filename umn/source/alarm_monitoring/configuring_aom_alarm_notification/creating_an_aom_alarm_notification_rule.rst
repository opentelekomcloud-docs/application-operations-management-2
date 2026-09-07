:original_name: mon_01_0015.html

.. _mon_01_0015:

Creating an AOM Alarm Notification Rule
=======================================

You can create an alarm notification rule and associate it with an SMN topic and a message template. If the log/resource/metric data meets the alarm condition, the system sends an alarm notification based on the associated SMN topic and message template.

Prerequisites
-------------

-  You have created a topic.
-  You have configured a topic policy.
-  You have added a subscriber (that is, an email or SMS message recipient) for the topic.
-  To obtain SMN topics when creating a notification rule, you must obtain the **smn:topic:list** permission in advance.

Constraints
-----------

-  You can create a maximum of 1,000 alarm notification rules. If the number of rules reaches 1,000, delete unnecessary ones.

Creating an Alarm Notification Rule
-----------------------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Alarm Center** > **Alarm Notification**.

#. On the displayed page, click **Create**.

#. Set the notification rule name, type, and other parameters by referring to :ref:`Table 1 <mon_01_0015__table133819502309>`.

   .. _mon_01_0015__table133819502309:

   .. table:: **Table 1** Parameters for configuring an alarm notification rule

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================================================+
      | Notification Rule Name            | Name of the rule. Enter up to 100 characters and do not start or end with an underscore (_) or hyphen (-). Only digits, letters, hyphens, and underscores are allowed.                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | Enterprise project.                                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                               |
      |                                   | -  If you have selected **All** for **Enterprise Project** on the global settings page, select one from the drop-down list here.                                                                              |
      |                                   | -  If you have already selected an enterprise project on the global settings page, this option will be dimmed and cannot be changed.                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the rule. Enter up to 1,024 characters.                                                                                                                                                        |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rule Type                         | Notification rule type.                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                               |
      |                                   | -  **Prometheus monitoring**                                                                                                                                                                                  |
      |                                   |                                                                                                                                                                                                               |
      |                                   |    If a metric or event meets the alarm condition, the system sends an alarm notification based on the associated SMN topic and message template.                                                             |
      |                                   |                                                                                                                                                                                                               |
      |                                   | -  **Log monitoring**                                                                                                                                                                                         |
      |                                   |                                                                                                                                                                                                               |
      |                                   |    If the log data meets the alarm condition, the system sends an alarm notification based on the associated SMN topic and message template.                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Topic                             | SMN topic. Select your desired topic from the drop-down list.                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                               |
      |                                   | If there is no topic you want to select, create one on the SMN console.                                                                                                                                       |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Message Template                  | Notification message template. Select your desired template from the drop-down list.                                                                                                                          |
      |                                   |                                                                                                                                                                                                               |
      |                                   | AOM provides preset message templates. If the preset templates do not meet requirements, click **Create Template** to create one. For details, see :ref:`Creating AOM Alarm Message Templates <mon_01_0016>`. |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

5. After the settings are complete, click **OK**. The rule is created. You can then perform the following operations:

   -  Go to the **Alarm Noise Reduction** page, :ref:`create a grouping rule <mon_01_0019>`, and associate it with the notification rule.
   -  Go to the **Alarm Rules** page, :ref:`create an alarm rule <mon_01_0006>`, and associate it with the notification rule.

More Operations
---------------

After an alarm notification rule is created, you can perform operations described in :ref:`Table 2 <mon_01_0015__en-us_topic_0169698264_table14918185010104>`.

.. _mon_01_0015__en-us_topic_0169698264_table14918185010104:

.. table:: **Table 2** Related operations

   +------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                                | Description                                                                                                                                                   |
   +==========================================+===============================================================================================================================================================+
   | Editing an alarm notification rule       | Click **Modify** in the **Operation** column.                                                                                                                 |
   +------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deleting an alarm notification rule      | -  To delete a single rule, click **Delete** in the **Operation** column in the row that contains the rule, and then click **Yes** on the displayed page.     |
   |                                          | -  To delete one or more rules, select them, click **Delete** above the rule list, and then click **Yes** on the displayed page.                              |
   |                                          |                                                                                                                                                               |
   |                                          | Precautions:                                                                                                                                                  |
   |                                          |                                                                                                                                                               |
   |                                          | -  Delete the bound alarm rules or grouping rules before deleting alarm notification rules.                                                                   |
   |                                          | -  If an alarm notification rule is deleted, alarm notifications cannot be received in a timely manner.                                                       |
   |                                          | -  To delete alarm notification rules in batches, ensure that they are under the same enterprise project.                                                     |
   +------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Searching for an alarm notification rule | You can filter alarm notification rules by rule name, description, type, enterprise project, message template, and update time, or enter a keyword to search. |
   +------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------+
