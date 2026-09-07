:original_name: mon_01_0021.html

.. _mon_01_0021:

Creating an AOM Alarm Silence Rule
==================================

Alarm silence rules can mask alarm notifications in specified periods.

Constraints
-----------

-  You can create a maximum of 100 silence rules. If this number has been reached, delete unnecessary rules.

-  Once a silence rule is created, it takes effect immediately.

Procedure
---------

#. Log in to the AOM 2.0 console.
#. In the navigation pane, choose **Alarm Center** > **Alarm Noise Reduction**.
#. On the **Silence Rules** tab page, click **Create** and set parameters such as the rule name and silence condition.

   .. table:: **Table 1** Setting a silence rule

      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Category              | Parameter             | Description                                                                                                                                                                                                                                                                                                                 |
      +=======================+=======================+=============================================================================================================================================================================================================================================================================================================================+
      | ``-``                 | Rule Name             | Name of a silence rule.                                                                                                                                                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                                                                                                                                             |
      |                       |                       | Enter up to 100 characters and do not start or end with an underscore (_). Only letters, digits, and underscores are allowed.                                                                                                                                                                                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Enterprise Project    | Enterprise project.                                                                                                                                                                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                                                                                                                                                             |
      |                       |                       | -  If you have selected **All** for **Enterprise Project** on the global settings page, select one from the drop-down list here.                                                                                                                                                                                            |
      |                       |                       | -  If you have already selected an enterprise project on the global settings page, this option will be grayed and cannot be changed.                                                                                                                                                                                        |
      |                       |                       | -  To use the enterprise project function, contact engineers.                                                                                                                                                                                                                                                               |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Description           | Description of a silence rule. Enter up to 1,024 characters.                                                                                                                                                                                                                                                                |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Silence Rule          | Silence Condition     | Any alarm notifications that meet the silence condition will be shielded.                                                                                                                                                                                                                                                   |
      |                       |                       |                                                                                                                                                                                                                                                                                                                             |
      |                       |                       | Value range and description:                                                                                                                                                                                                                                                                                                |
      |                       |                       |                                                                                                                                                                                                                                                                                                                             |
      |                       |                       | -  **Alarm Severity**: severity of a metric or event alarm. Options: **Critical**, **Major**, **Minor**, and **Warning**. Example: **Alarm Severity** **Equals to** **Critical**                                                                                                                                            |
      |                       |                       | -  **Resource Type**: resource type selected when you create an alarm rule or customize alarm reporting. Options: include **host**, **container**, and **process**. Example: **Resource Type** **Equals to** **container**                                                                                                  |
      |                       |                       | -  **Alarm Source**: name of the service that triggers the alarm or event. Options: include **AOM**, **LTS**, and **CCE**. Example: **Alarm Source** **Equals to** **AOM**                                                                                                                                                  |
      |                       |                       | -  **Tag**: alarm identification attribute, which consists of the tag name and tag value and can be customized. Example: **Tag** **aom_monitor_level** **Equals to** **infrastructure**                                                                                                                                     |
      |                       |                       | -  *XX* **Exists**: indicates the alarm whose metadata contains parameter *XX*. Example: For **Alarm Source** **Exists**, the alarms whose metadata contains the provider will be filtered.                                                                                                                                 |
      |                       |                       | -  *XX* **Regular Expression**: indicates the alarm whose parameter *XX* matches the regular expression. Example: For **Resource Type** **Regular Expression** **host\***, the alarms whose resource type contains **host** will be filtered.                                                                               |
      |                       |                       |                                                                                                                                                                                                                                                                                                                             |
      |                       |                       | Rule description:                                                                                                                                                                                                                                                                                                           |
      |                       |                       |                                                                                                                                                                                                                                                                                                                             |
      |                       |                       | You can create up to 10 parallel conditions under **Silence Condition**, and up to 10 serial conditions under each parallel condition. Serial conditions are in the AND relationship whereas parallel conditions are in the OR relationship. An alarm must meet all serial conditions under one of the parallel conditions. |
      |                       |                       |                                                                                                                                                                                                                                                                                                                             |
      |                       |                       | Example: If **Alarm Severity** is set to **Warning** in a serial condition, warnings will be shielded.                                                                                                                                                                                                                      |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      |                       | Silence Time          | Time when alarm notifications are shielded. There are two options:                                                                                                                                                                                                                                                          |
      |                       |                       |                                                                                                                                                                                                                                                                                                                             |
      |                       |                       | -  **Fixed time**: Alarm notifications are shielded only in a specified period.                                                                                                                                                                                                                                             |
      |                       |                       | -  **Cycle time**: Alarm notifications are shielded periodically.                                                                                                                                                                                                                                                           |
      +-----------------------+-----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **Confirm**.

More Operations
---------------

After creating a silence rule, you can also perform the operations listed in :ref:`Table 2 <mon_01_0021__en-us_topic_0169698264_table14918185010104>`.

.. _mon_01_0021__en-us_topic_0169698264_table14918185010104:

.. table:: **Table 2** Related operations

   +-----------------------------------+-------------------------------------------------------------------------------------------------------------+
   | Operation                         | Description                                                                                                 |
   +===================================+=============================================================================================================+
   | Modifying a silence rule          | Click **Modify** in the **Operation** column.                                                               |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------+
   | Deleting a silence rule           | -  To delete a single rule, click **Delete** in the **Operation** column in the row that contains the rule. |
   |                                   | -  To delete one or more rules, select them and click **Delete** above the rule list.                       |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------+
   | Searching for a silence rule      | Enter a rule name in the search box in the upper right corner and click |image1|.                           |
   +-----------------------------------+-------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002370949721.png
