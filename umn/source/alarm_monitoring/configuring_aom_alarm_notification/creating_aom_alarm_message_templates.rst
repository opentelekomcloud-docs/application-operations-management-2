:original_name: mon_01_0016.html

.. _mon_01_0016:

Creating AOM Alarm Message Templates
====================================

In AOM, you can create message templates to customize notifications. When a preset notification rule is triggered, notifications can be sent to specified personnel by email, SMS, HTTP, or HTTPS.

Function Introduction
---------------------

-  Message templates for emails, SMS, HTTP, and HTTPS are supported.
-  You can customize message templates. For details, see :ref:`3.c <mon_01_0016__li153081748171720>`.

Constraints
-----------

-  You can create a maximum of 100 metric/event (Prometheus monitoring) or log (log monitoring) message templates. If the number of message templates of a certain type reaches 100, delete unnecessary ones.
-  AOM provides preset message templates. They cannot be deleted or edited. If there is no custom message template, notifications are sent based on a preset message template by default.
-  If no message template is created, the default message template will be used.

.. _mon_01_0016__section98731914104516:

Creating a Message Template
---------------------------

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, choose **Alarm Center** > **Alarm Notification**.
#. On the **Message Templates** tab page, click **Create**.

   a. Enter a template name, message template type, and description, and specify an enterprise project.

      .. table:: **Table 1** Parameter description

         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                      |
         +===================================+==================================================================================================================================================================================+
         | Template Name                     | Name of a message template. Enter up to 100 characters and do not start or end with an underscore (_) or hyphen (-). Only digits, letters, underscores, and hyphens are allowed. |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Description                       | Description of the template. Enter up to 1024 characters.                                                                                                                        |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Message Template                  | Type of the message template. Option: **Prometheus monitoring** or **Log monitoring**.                                                                                           |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Enterprise Project                | Enterprise project.                                                                                                                                                              |
         |                                   |                                                                                                                                                                                  |
         |                                   | -  If you have selected **All** for **Enterprise Project** on the global settings page, select one from the drop-down list here.                                                 |
         |                                   | -  If you have already selected an enterprise project on the global settings page, this option will be dimmed and cannot be changed.                                             |
         +-----------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   b. Select a language (for example, English).

   c. .. _mon_01_0016__li153081748171720:

      Customize the template content (default fields are automatically filled in when a Prometheus monitoring template is created). There are templates for emails/SMS. For details about Prometheus monitoring message templates, see :ref:`Table 2 <mon_01_0016__table12639440194518>`. For details about log monitoring message templates, see :ref:`Table 3 <mon_01_0016__en-us_topic_0000001159394194_table13241557318>`.

      -  In addition to the message fields in the default template, the message template also supports custom fields. You need to specify the fields when reporting event alarms.
      -  Custom fields support the JSONPath format. Example: **$event.metadata.case1** or **$event.metadata.case[0]**.
      -  In the upper right corner of the **Body** area, click **Add Variables** to copy required variables.
      -  The **TMS tag: $event.annotations.tms_tags** variable configured in the alarm message template takes effect only after :ref:`TMS Tag Display <mon_01_0110__section633611121560>` is enabled.
      -  If you select **Emails**, you can click **Preview** to view the final effect. On the **Preview** page, change the message topic if necessary.

      .. _mon_01_0016__table12639440194518:

      .. table:: **Table 2** Variables in the default message template

         +---------------------+----------------------------------------------------------------------------------------+----------------------------+
         | Variable            | Description                                                                            | Definition                 |
         +=====================+========================================================================================+============================+
         | Alarm Name          | Name of the alarm rule that is triggered.                                              | ${event_name_alias}        |
         +---------------------+----------------------------------------------------------------------------------------+----------------------------+
         | Alarm ID            | ID of the alarm rule that is triggered.                                                | ${id}                      |
         +---------------------+----------------------------------------------------------------------------------------+----------------------------+
         | Notification Rule   | Name of the alarm notification rule.                                                   | ${action_rule}             |
         +---------------------+----------------------------------------------------------------------------------------+----------------------------+
         | Occurred            | Time when the alarm or event is triggered.                                             | ${starts_at}               |
         +---------------------+----------------------------------------------------------------------------------------+----------------------------+
         | Event Severity      | Alarm or event severity. Options: **Critical**, **Major**, **Minor**, and **Warning**. | ${event_severity}          |
         +---------------------+----------------------------------------------------------------------------------------+----------------------------+
         | Alarm Info          | Detailed alarm information.                                                            | ${alarm_info}              |
         +---------------------+----------------------------------------------------------------------------------------+----------------------------+
         | Resource Identifier | Resource for which the alarm or event is triggered.                                    | ${resources_new}           |
         +---------------------+----------------------------------------------------------------------------------------+----------------------------+
         | Suggestion          | Suggestion about handing the alarm. For non-custom reporting, "NA" is displayed.       | ${alarm_fix_suggestion_zh} |
         +---------------------+----------------------------------------------------------------------------------------+----------------------------+

      .. _mon_01_0016__en-us_topic_0000001159394194_table13241557318:

      .. table:: **Table 3** Log message template parameters

         +-----------------+------------------+------------------------------------------------------------------------------------------------------+-------------------+
         | Parameter       | Description      | Check Rule                                                                                           | Example           |
         +=================+==================+======================================================================================================+===================+
         | Topic           | Message topic.   | Customize the topic name or use variables. (Max. 512 characters)                                     | test              |
         |                 |                  |                                                                                                      |                   |
         |                 |                  | Only email templates need a topic name.                                                              |                   |
         +-----------------+------------------+------------------------------------------------------------------------------------------------------+-------------------+
         | Body            | Message content. | **Add variables:**                                                                                   | ${event_name}     |
         |                 |                  |                                                                                                      |                   |
         |                 |                  | -  Original rule name: *${event_name}*                                                               | ${event_severity} |
         |                 |                  | -  Alarm severity: *${event_severity}*                                                               |                   |
         |                 |                  | -  Occurrence time: *${starts_at}*                                                                   | ${starts_at}      |
         |                 |                  | -  Occurrence region: *${region_name}*                                                               |                   |
         |                 |                  | -  Account: *${domain_name}*                                                                         | ${region_name}    |
         |                 |                  | -  Alarm source: *$event.metadata.resource_provider*                                                 |                   |
         |                 |                  | -  Resource type: *$event.metadata.resource_type*                                                    |                   |
         |                 |                  | -  Resource ID: *${resources}*                                                                       |                   |
         |                 |                  | -  Alarm status: *$event.annotations.alarm_status*                                                   |                   |
         |                 |                  | -  Expression: *$event.annotations.condition_expression*                                             |                   |
         |                 |                  | -  Current value: *$event.annotations.current_value*                                                 |                   |
         |                 |                  | -  Statistical period: *$event.annotations.frequency*                                                |                   |
         |                 |                  | -  Rule name: *$event.annotations.alarm_rule_alias*                                                  |                   |
         |                 |                  | -  Keyword variables                                                                                 |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |    #. Query time: *$event.annotations.results[0].time*                                               |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |    #. Query logs:                                                                                    |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |       *$event.annotations.results[0].raw_results*                                                    |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |    #. Query URL:                                                                                     |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |       *$event.annotations.results[0].url*                                                            |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |    #. Log group/stream name: *$event.annotations.results[0].resource_id*                             |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |       **Only the original name of the log group or stream created for the first time can be added.** |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  | -  SQL variables                                                                                     |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |    #. Log group/stream names of chart 0: *$event.annotations.results[0].resource_id*                 |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |       **Only the original name of the log group or stream created for the first time can be added.** |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |    #. Query statement of chart 0: *$event.annotations.results[0].sql*                                |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |    #. Query time of chart 0: *$event.annotations.results[0].time*                                    |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |    #. Query URL of chart 0: *$event.annotations.results[0].url*                                      |                   |
         |                 |                  |                                                                                                      |                   |
         |                 |                  |    #. Query logs of chart 0: *$event.annotations.results[0].raw_results*                             |                   |
         +-----------------+------------------+------------------------------------------------------------------------------------------------------+-------------------+

   d. Click **Confirm**. The message template is created.

More Operations
---------------

After creating a message template, you can perform the operations listed in :ref:`Table 4 <mon_01_0016__en-us_topic_0169698264_table14918185010104>`.

.. _mon_01_0016__en-us_topic_0169698264_table14918185010104:

.. table:: **Table 4** Related operations

   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                         | Description                                                                                                                                                               |
   +===================================+===========================================================================================================================================================================+
   | Editing a message template        | Click **Edit** in the **Operation** column.                                                                                                                               |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Copying a message template        | Click **Copy** in the **Operation** column.                                                                                                                               |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deleting a message template       | -  To delete a single message template, click **Delete** in the **Operation** column in the row that contains the template, and then click **Yes** on the displayed page. |
   |                                   | -  To delete one or more message templates, select them, click **Delete** above the template list, and then click **Yes** on the displayed page.                          |
   |                                   |                                                                                                                                                                           |
   |                                   | **Before deleting a message template, delete the alarm notification rules bound to it.**                                                                                  |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Searching for a message template  | You can search for message templates by template name, description, type, and update time, or enter a keyword to search for message templates.                            |
   +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
