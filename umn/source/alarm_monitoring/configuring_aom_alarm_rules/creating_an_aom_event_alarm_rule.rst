:original_name: mon_01_0010.html

.. _mon_01_0010:

Creating an AOM Event Alarm Rule
================================

You can set event conditions for services by setting event alarm rules. When the resource data meets an event condition, an event alarm is generated.

Constraints
-----------

-  If you want to receive email/SMS notifications when the resource data meets the event condition, set an alarm notification rule by referring to :ref:`Creating an AOM Alarm Notification Rule <mon_01_0015>`.
-  A maximum of 3,000 metric/event alarm rules can be created.
-  When setting an alarm notification policy, enabling alarm noise reduction and associating the policy with a grouping rule are not recommended. This is because accumulated triggering is similar to alarm noise reduction.

Procedure
---------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Alarm Center** > **Alarm Rules**.

#. On the displayed page, click **Create Alarm Rule**.

#. Set basic information about the alarm rule by referring to :ref:`Table 1 <mon_01_0010__mon_01_0008_table1730711167518>`.

   .. _mon_01_0010__mon_01_0008_table1730711167518:

   .. table:: **Table 1** Basic information

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                                                               |
      +===================================+===========================================================================================================================================================================================================================================+
      | Original Rule Name                | Original name of the alarm rule.                                                                                                                                                                                                          |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | Enter a maximum of 256 characters and do not start or end with any special character. Only letters, digits, underscores (_), and hyphens (-) are allowed.                                                                                 |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rule Name                         | Name of a rule. Max.: 256 characters. Only letters, digits, hyphens (-), and underscores (_) are allowed. Do not start or end with a hyphen or underscore.                                                                                |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | .. note::                                                                                                                                                                                                                                 |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   |    -  If you set **Rule Name**, it will be displayed preferentially.                                                                                                                                                                      |
      |                                   |    -  After an alarm rule is created, you can change **Rule Name** but cannot change **Original Rule Name**. When you change **Rule Name** and then move the cursor over it, both **Original Rule Name** and **Rule Name** can be viewed. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | Enterprise project.                                                                                                                                                                                                                       |
      |                                   |                                                                                                                                                                                                                                           |
      |                                   | -  If you have selected **All** for **Enterprise Project** on the global settings page, select one from the drop-down list here.                                                                                                          |
      |                                   | -  If you have already selected an enterprise project on the global settings page, this option will be dimmed and cannot be changed.                                                                                                      |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Description                       | Description of the rule. Enter up to 1,024 characters.                                                                                                                                                                                    |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Set the detailed information about the alarm rule.

   a. Set **Rule Type** to **Event alarm rule**.
   b. Specify an event type and source.

      -  **System**: events ingested to AOM by default. Options: CCE/IoTDA/ModelArts.
      -  **Custom**: third-party service events ingested to AOM. Select an event source from the existing service list.

   c. Set alarm rule details.

      .. table:: **Table 2** Alarm rule parameters

         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Parameter                         | Description                                                                                                                                                                                                                                                                                                                                                                       |
         +===================================+===================================================================================================================================================================================================================================================================================================================================================================================+
         | Monitored Object                  | Select criteria to filter service events. You can select **Notification Type**, **Event Name**, **Alarm Severity**, **Custom Attributes**, **Namespace**, or **Cluster Name** as the filter criterion. One or more criteria can be selected.                                                                                                                                      |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                   |
         |                                   | **Set Event Name as the filter criterion. If no event name is selected, all events are selected by default.**                                                                                                                                                                                                                                                                     |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Alarm Condition                   | Condition for triggering event alarms. It contains:                                                                                                                                                                                                                                                                                                                               |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                   |
         |                                   | -  **Event Name**: The value varies depending on **Monitored Object**. If you do not specify any event for **Monitored Object**, all events are displayed here and cannot be changed.                                                                                                                                                                                             |
         |                                   | -  **Trigger Mode**: trigger mode of an event alarm.                                                                                                                                                                                                                                                                                                                              |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                   |
         |                                   |    -  **Accumulated Trigger**: A notification is triggered at a preset frequency after an event or alarm trigger condition is met for a specified number of times. If **Alarm Frequency** is set to **N/A**, there is no limit on the number of notifications. That is, one notification is sent when an event or alarm trigger condition is met for a specified number of times. |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                   |
         |                                   |       Assume that you set **Event Name** to **VolumeResizeFailed**, **Monitoring Period** to **20 minutes**, **Cumulative Times** to **>= 3**, and **Alarm Frequency** to **Every 5 minutes**. If data volume scale-out fails for three or more times within 20 minutes, an alarm notification will be sent every five minutes unless the alarm is cleared.                       |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                   |
         |                                   |       **If you have selected** **Alarm noise reduction** when :ref:`setting the alarm notification policy <mon_01_0010__li15513123154817>`, the alarm frequency set here does not take effect. Alarm notifications are sent at the frequency set during noise reduction configuration.                                                                                            |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                   |
         |                                   |    -  **Immediate Trigger**: A notification is triggered immediately after an event or alarm trigger condition is met.                                                                                                                                                                                                                                                            |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                   |
         |                                   | -  **Alarm Severity**: severity of an event alarm. Options:                                                                                                                                                                                                                                                                                                                       |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                   |
         |                                   |    -  |image1|: critical alarm.                                                                                                                                                                                                                                                                                                                                                   |
         |                                   |    -  |image2|: major alarm.                                                                                                                                                                                                                                                                                                                                                      |
         |                                   |    -  |image3|: minor alarm.                                                                                                                                                                                                                                                                                                                                                      |
         |                                   |    -  |image4|: warning.                                                                                                                                                                                                                                                                                                                                                          |
         |                                   |                                                                                                                                                                                                                                                                                                                                                                                   |
         |                                   | In case of multiple events, click **Batch Set** to set alarm conditions for these events in batches.                                                                                                                                                                                                                                                                              |
         +-----------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. .. _mon_01_0010__li15513123154817:

   Set an alarm notification policy. There are two alarm notification modes. Select one as required.

   -  **Direct alarm reporting**: An alarm is directly sent when the alarm condition is met.

      Enable **Notification Rule** and select a notification rule. (If **Notification Rule** is disabled, the alarm rule cannot be created.) The system sends alarm notifications based on the associated SMN topic and message template. If existing alarm notification rules cannot meet your requirements, create one. For details about how to set alarm notification rules, see :ref:`Creating an AOM Alarm Notification Rule <mon_01_0015>`.

   -  **Alarm noise reduction**: Alarms are sent only after being processed based on noise reduction rules, preventing alarm storms.

      Enable **Grouping Rule** and select a grouping rule. (If **Grouping Rule** is disabled, the alarm rule cannot be created.) If existing grouping rules cannot meet your requirements, click **Create Rule** in the drop-down list to create one. For details, see :ref:`Creating an AOM Alarm Grouping Rule <mon_01_0019>`. **The alarm severity and tag configured in the selected grouping rule must match those configured in the alarm rule. Otherwise, the grouping rule does not take effect.**

#. Click **Confirm**. Then click **View Rule** to view the created alarm rule.

   When CCE resources meet the configured event alarm conditions, an event alarm will be generated on the alarm page. To view it, choose **Alarm Center** > **Alarm List** in the navigation pane. The system also sends alarm notifications to specified personnel by email or SMS.

.. |image1| image:: /_static/images/en-us_image_0000002337031960.png
.. |image2| image:: /_static/images/en-us_image_0000002370950169.png
.. |image3| image:: /_static/images/en-us_image_0000002370950157.png
.. |image4| image:: /_static/images/en-us_image_0000002337031956.png
