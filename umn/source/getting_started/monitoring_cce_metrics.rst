:original_name: aom_00_0003.html

.. _aom_00_0003:

Monitoring CCE Metrics
======================

Cloud Container Engine (CCE) is an enterprise-level cluster hosting service. It allows you to quickly build reliable container clusters based on cloud servers, and easily create and manage different containerized workloads. AOM is a one-stop, multi-dimensional O&M platform for cloud applications. It enables you to monitor real-time running of applications, resources, and services and detect faults in a timely manner, improving O&M efficiency. After CCE is interconnected with AOM, CCE cluster information can be reported to AOM. AOM can monitor the status and performance of CCE clusters and provide alarm notifications in real time.

You can set alarm rules in AOM to check whether resources in CCE clusters are normal and learn about real-time cluster running. This section uses **aom_container_cpu_usage** as an example to describe how to set an alarm rule.

Procedure
---------

#. :ref:`Subscribing to AOM 2.0 for the First Time and Granting Permissions <aom_00_0003__section849614531181>`
#. :ref:`Monitoring Containers <aom_00_0003__section811053204710>`: Purchase a cluster and node on CCE. The ICAgent is then automatically installed to report cluster metrics to AOM.
#. :ref:`Setting an Alarm Notification Rule <aom_00_0003__section291715218147>`: Create an alarm notification rule and associate it with an SMN topic and a message template. If the CCE metric data meets the alarm condition, the system sends an alarm notification accordingly. If you do not want to receive alarm notifications by email or SMS, there is no need to set alarm notification rules.
#. :ref:`Setting an Alarm Rule <aom_00_0003__section51417537472>`: Create an alarm rule for the CCE metric. If the metric data meets the alarm condition, an alarm will be generated.

Preparation
-----------

This section uses a CCE metric as an example. You need to purchase a cluster and node in CCE in advance. If you already have a cluster and node, skip this step.

.. _aom_00_0003__section849614531181:

Subscribing to AOM 2.0 for the First Time and Granting Permissions
------------------------------------------------------------------

#. Register an account and perform real-name authentication.

   Before using AOM 2.0, register an account and perform real-name authentication.

#. Subscribe to AOM 2.0.

   Before using AOM 2.0, subscribe to it. If you have subscribed to AOM 2.0, skip the following operations.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner and select your desired region from the drop-down list.
   c. Click |image2| on the left and choose **Application** > **Application Operations Management**. In the navigation pane on the left, choose **AOM 2.0**. The AOM 2.0 page is displayed.
   d. On the displayed **Service Authorization** page, read the *Authorization Statement* and select "I have read and agreed to the *Authorization Statement*".
   e. Click **Subscribe and Authorize for Free** for AOM 2.0.

#. Grant the AOM and CCE permissions to the user.

   Ensure that **AOM FullAccess** and **CCE FullAccess** permissions are granted.

.. _aom_00_0003__section811053204710:

Monitoring Containers
---------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Infrastructure Monitoring** > **Container Insights** > **Workload Monitoring**.

#. .. _aom_00_0003__li68781949194410:

   Click a workload on any workload tab page. The workload details such as the name, status, cluster, and namespace are displayed. For example, monitor workload **coredns**, which belongs to cluster **aom-doc-test**.

   You can also create more workloads to monitor.

.. _aom_00_0003__section291715218147:

Setting an Alarm Notification Rule
----------------------------------

#. In the navigation pane, choose **Alarm Center** > **Alarm Notification**.

#. On the **Notification Rules** tab page, click **Create**. On the displayed page, set parameters by referring to :ref:`Table 1 <aom_00_0003__en-us_topic_0000001222242764_table851894218585>`.

   .. _aom_00_0003__en-us_topic_0000001222242764_table851894218585:

   .. table:: **Table 1** Alarm notification rule parameters

      +------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter              | Description                                                                                                                                                                              | Example               |
      +========================+==========================================================================================================================================================================================+=======================+
      | Notification Rule Name | Name of an alarm notification rule. Enter up to 100 characters and do not start or end with an underscore (_) or hyphen (-). Only digits, letters, underscores, and hyphens are allowed. | Mon_aom               |
      +------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Enterprise Project     | Select the required enterprise project. The default value is **default**.                                                                                                                | default               |
      |                        |                                                                                                                                                                                          |                       |
      |                        | -  If you have selected **All** for **Enterprise Project** on the global settings page, select one from the drop-down list here.                                                         |                       |
      |                        | -  If you have already selected an enterprise project on the global settings page, this option will be grayed and cannot be changed.                                                     |                       |
      +------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description            | Description of the notification rule. Enter up to 1,024 characters. In this example, leave this parameter blank.                                                                         | ``-``                 |
      +------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Rule Type              | Type of an alarm notification rule. Select **Prometheus monitoring** in this example.                                                                                                    | Prometheus monitoring |
      |                        |                                                                                                                                                                                          |                       |
      |                        | **Prometheus monitoring**: If a metric or an event meets the alarm condition, the system sends an alarm notification based on the associated SMN topic and message template.             |                       |
      +------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Topic                  | SMN topic. Select a desired topic from the drop-down list.                                                                                                                               | ``-``                 |
      |                        |                                                                                                                                                                                          |                       |
      |                        | If there is no topic you want to select, create one on the SMN console.                                                                                                                  |                       |
      +------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Message Template       | Notification message template. Select your desired template from the drop-down list.                                                                                                     | ``-``                 |
      |                        |                                                                                                                                                                                          |                       |
      |                        | If there is no message template you want to select, create one.                                                                                                                          |                       |
      +------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

.. _aom_00_0003__section51417537472:

Setting an Alarm Rule
---------------------

Metric alarm rules can be created using the following modes: **Select from all metrics** and **PromQL**.

The following uses **Select from all metrics** as an example.

#. In the navigation pane, choose **Alarm Center** > **Alarm Rules**. Then, click **Create Alarm Rule**.

#. Set basic information about the alarm rule by referring to :ref:`Table 2 <aom_00_0003__en-us_topic_0000001582534348_table1730711167518>`.

   .. _aom_00_0003__en-us_topic_0000001582534348_table1730711167518:

   .. table:: **Table 2** Basic information

      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                         | Example               |
      +=======================+=====================================================================================================================================================================================+=======================+
      | Original Rule Name    | Original name of a rule. Enter a maximum of 256 characters and do not start or end with underscores (_) or hyphens (-). Only letters, digits, underscores, and hyphens are allowed. | monitor_cce           |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Rule Name             | Name of a rule. Enter a maximum of 256 characters and do not start or end with underscores (_) or hyphens (-). Only letters, digits, underscores, and hyphens are allowed.          | ``-``                 |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Enterprise Project    | Select the required enterprise project. The default value is **default**.                                                                                                           | default               |
      |                       |                                                                                                                                                                                     |                       |
      |                       | -  If you have selected **All** for **Enterprise Project** on the global settings page, select one from the drop-down list here.                                                    |                       |
      |                       | -  If you have already selected an enterprise project on the global settings page, this option will be grayed and cannot be changed.                                                |                       |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Description of the rule. Enter up to 1,024 characters. In this example, leave this parameter blank.                                                                                 | ``-``                 |
      +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Set the detailed information about the alarm rule.

   a. **Rule Type**: **Metric alarm rule**.

   b. **Configuration Mode**: **Select from all metrics**. Then you can set alarm conditions for different types of resources.

   c. Select a target Prometheus instance from the drop-down list. In this example, select **Prometheus_AOM_Default**.

   d. Set alarm rule details by referring to :ref:`Table 3 <aom_00_0003__en-us_topic_0000001582534348_table8512161614337>`.

      After the setting is complete, the monitored metric data is displayed in a line graph above the alarm conditions. You can click **Add Metric** to add more metrics and set the statistical period and detection rules for them.

      .. _aom_00_0003__en-us_topic_0000001582534348_table8512161614337:

      .. table:: **Table 3** Alarm rule details

         +--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
         | Parameter          | Description                                                                                                                                                                                                      | Example                                             |
         +====================+==================================================================================================================================================================================================================+=====================================================+
         | Multiple Metrics   | Calculation is performed based on the preset alarm conditions one by one. An alarm is triggered when one of the conditions is met.                                                                               | Multiple Metrics                                    |
         +--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
         | Metric             | Metric to be monitored. Click the **Metric** text box. In the resource tree on the right, you can select a target metric by resource type.                                                                       | aom_container_cpu_usage                             |
         +--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
         | Statistical Period | Interval at which metric data is collected.                                                                                                                                                                      | 1 minute                                            |
         +--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
         | Conditions         | Metric monitoring scope. If this parameter is left blank, all resources are covered. Set the condition based on the workload mentioned in :ref:`3 <aom_00_0003__li68781949194410>`.                              | Cluster name=aom-doc-test AND Workload name=coredns |
         +--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
         | Grouping Condition | Aggregate metric data by the specified field and calculate the aggregation result.                                                                                                                               | Not grouped                                         |
         +--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
         | Rule               | Detection rule of a metric alarm, which consists of the statistical mode (**Avg**, **Min**, **Max**, **Sum**, and **Samples**), determination criterion (**>=**, **<=**, **>**, and **<**), and threshold value. | Avg > 10                                            |
         +--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
         | Trigger Condition  | When the metric value meets the alarm condition for a specified number of consecutive periods, a metric alarm will be generated.                                                                                 | 3                                                   |
         +--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+
         | Alarm Severity     | Severity of a metric alarm.                                                                                                                                                                                      | |image4|                                            |
         +--------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------+

#. Click **Advanced Settings** and set information such as **Check Interval** and **Alarm Clearance**. For details about the parameters, see :ref:`Table 4 <aom_00_0003__en-us_topic_0000001582534348_table55151160338>`.

   .. _aom_00_0003__en-us_topic_0000001582534348_table55151160338:

   .. table:: **Table 4** Advanced settings

      +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                          | Description                                                                                                                                                                                                                             | Example                                                                                                                           |
      +====================================+=========================================================================================================================================================================================================================================+===================================================================================================================================+
      | Check Interval                     | Interval at which metric query and analysis results are checked.                                                                                                                                                                        | Custom interval: 1 minute                                                                                                         |
      +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Alarm Clearance                    | The alarm will be cleared when the alarm condition is not met for a specified number of consecutive periods.                                                                                                                            | 1                                                                                                                                 |
      +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Action Taken for Insufficient Data | Action to be taken if there is no or insufficient metric data within the monitoring period. Enable this option if needed.                                                                                                               | Enabled: If the data is insufficient for **1** period, the status will change to **Insufficient data** and an alarm will be sent. |
      +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Tags                               | Click |image5| to add an alarm rule tag. It is an alarm identification attribute in the format of "key:value". It is used in alarm noise reduction scenarios. In this example, leave this parameter blank.                              | ``-``                                                                                                                             |
      |                                    |                                                                                                                                                                                                                                         |                                                                                                                                   |
      |                                    | For details, see :ref:`Alarm Tags and Annotations <mon_01_0044>`.                                                                                                                                                                       |                                                                                                                                   |
      +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Annotations                        | Click |image6| to add an alarm rule annotation. It is an alarm non-identification attribute in the format of "key:value". It is used in alarm notification and message template scenarios. In this example, leave this parameter blank. | ``-``                                                                                                                             |
      |                                    |                                                                                                                                                                                                                                         |                                                                                                                                   |
      |                                    | For details, see :ref:`Alarm Tags and Annotations <mon_01_0044>`.                                                                                                                                                                       |                                                                                                                                   |
      +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+

#. Set an alarm notification policy. For details, see :ref:`Table 5 <aom_00_0003__table18775831101314>`.

   .. _aom_00_0003__table18775831101314:

   .. table:: **Table 5** Alarm notification policy parameters

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                             | Example                                            |
      +=======================+=========================================================================================================================================================================================================================================================================================================================================================================================================+====================================================+
      | Notify When           | Set the scenario for sending alarm notifications. By default, **Alarm triggered** and **Alarm cleared** are selected.                                                                                                                                                                                                                                                                                   | Retain the default value.                          |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                         |                                                    |
      |                       | -  **Alarm triggered**: If the alarm trigger condition is met, the system sends an alarm notification to the specified personnel by email or SMS.                                                                                                                                                                                                                                                       |                                                    |
      |                       | -  **Alarm cleared**: If the alarm clearance condition is met, the system sends an alarm notification to the specified personnel by email or SMS.                                                                                                                                                                                                                                                       |                                                    |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+
      | Alarm Mode            | -  **Direct alarm reporting**: An alarm is directly sent when the alarm condition is met. If you select this mode, set an interval for notification and specify whether to enable a notification rule.                                                                                                                                                                                                  | **Alarm Mode**: Select **Direct alarm reporting**. |
      |                       | -  **Frequency**: frequency for sending alarm notifications. Select a desire value from the drop-down list.                                                                                                                                                                                                                                                                                             |                                                    |
      |                       | -  **Notification Rule**: After the rule is enabled, the system sends notifications based on the associated SMN topic and message template. If there is no alarm notification rule you want to select, click **Add Rule** in the drop-down list to create one. For details about how to set alarm notification rules, see :ref:`Setting an Alarm Notification Rule <aom_00_0003__section291715218147>`. | **Frequency**: Select **Once**.                    |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                         |                                                    |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                         | **Notification Rule**: **Mon_aom**                 |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------+

#. Click **Confirm**. Then click **View Rule** to view the created rule.

   In the expanded list, if a metric value meets the configured alarm condition, a metric alarm is generated on the alarm page. To view the alarm, choose **Alarm Center** > **Alarm List** in the navigation pane. If a metric value meets the preset notification policy, the system sends an alarm notification to the specified personnel by email or SMS.

Related Information
-------------------

After an alarm rule is configured, you can perform the following operations if needed:

-  On the workload details page, click the **Alarms** tab to check alarms. Alternatively, choose **Alarm Center** > **Alarm List** to check alarms. For details, see :ref:`Checking AOM Alarms or Events <mon_01_0011>`.
-  Create metric alarm rules in different ways. For details, see :ref:`Creating an AOM Metric Alarm Rule <mon_01_0008>`.

.. |image1| image:: /_static/images/en-us_image_0000002370948209.png
.. |image2| image:: /_static/images/en-us_image_0000002371028357.png
.. |image3| image:: /_static/images/en-us_image_0000002336870272.png
.. |image4| image:: /_static/images/en-us_image_0000002336870272.png
.. |image5| image:: /_static/images/en-us_image_0000002370948265.png
.. |image6| image:: /_static/images/en-us_image_0000002370948205.png
