:original_name: aom_00_0007.html

.. _aom_00_0007:

Using Prometheus to Monitor ECS Metrics
=======================================

An Elastic Cloud Server (ECS) is a computing server consisting of the CPU, memory, OS, and Elastic Volume Service (EVS) disk. It supports on-demand allocation and auto scaling. ECSs integrate Virtual Private Cloud (VPC), security group, and Cloud Firewall (CFW) capabilities to create an efficient, reliable, and secure computing environment. This ensures stable and uninterrupted running of services. AOM is a one-stop, multi-dimensional O&M platform for cloud applications. It enables you to monitor real-time running of applications, resources, and services and detect faults in a timely manner, improving O&M efficiency. After an ECS is connected to AOM, AOM can monitor the ECS in real time and send alarm notifications.

This section uses the **node_network_up** metric of an ECS as an example to describe how to use AOM.

Constraints
-----------

The ECS must be in the same region as the AOM console.

Procedure
---------

#. :ref:`Installing UniAgent on the ECS <aom_00_0007__section5760211124410>`: Install UniAgent on the host in the region where the AOM console is located to centrally manage metric collection plug-ins.
#. :ref:`Creating a Host Group <aom_00_0007__en-us_topic_0000001988246261_en-us_topic_0000001118763740_section665755611241>`: Create a host group for better host management and more efficient data collection.
#. :ref:`Connecting an ECS to AOM <aom_00_0007__section1867918161483>`: Connect an ECS to AOM. Then you can install Node Exporter and configure collection tasks for the host group. The collected metrics will be stored in the Prometheus instance for ECS for easy management.
#. :ref:`Setting a Metric Alarm Rule <aom_00_0007__section51417537472>`: Create an alarm rule for the ECS metric. If the metric data meets the alarm condition, an alarm will be generated.

Prerequisites
-------------

-  You have purchased an ECS. If you already have an ECS, skip this step.
-  You have :ref:`subscribed to AOM 2.0 and granted permissions <aom_00_0003__section849614531181>`.

.. _aom_00_0007__section5760211124410:

Installing UniAgent on the ECS
------------------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Settings** > **Global Settings**.

#. On the displayed page, choose **Collection Settings** > **UniAgents** and click **Try New Version** in the upper right corner of the page.

#. On the displayed page, check the UniAgent status of the ECS.

   -  If the UniAgent status is **Running**, UniAgent has been installed. In this case, go to :ref:`Creating a Host Group <aom_00_0007__en-us_topic_0000001988246261_en-us_topic_0000001118763740_section665755611241>`.
   -  If the UniAgent status is **Offline**, UniAgent is abnormal.
   -  If the UniAgent status is **Installing**, UniAgent is being installed. Wait for UniAgent installation.
   -  If the UniAgent status is **Installation failed** or **Not installed**, UniAgent fails to be installed or is not installed on the host. In this case, install it.

#. On the **ECS** tab page, click **Install UniAgent** and then select the **Install via Script (Recommended)** scenario.

#. .. _aom_00_0007__en-us_topic_0000001944840874_en-us_topic_0000001860836318_li208691737122816:

   On the **Install UniAgent** page, set parameters.

   .. table:: **Table 1** Installation parameters

      +-----------------------------------+----------------------------------------------------------------------------------------------------+--------------------------------------+
      | Parameter                         | Description                                                                                        | Example                              |
      +===================================+====================================================================================================+======================================+
      | Server Region                     | Region where the target server is located.                                                         | Current region                       |
      |                                   |                                                                                                    |                                      |
      |                                   | **Current region**: The network between AOM and the server in the current region is connected.     |                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------+--------------------------------------+
      | Server Type                       | Options: **ECSs** and **Other Servers**. Select **ECSs**.                                          | ECSs                                 |
      |                                   |                                                                                                    |                                      |
      |                                   | **ECSs**: hosts managed by the ECS service.                                                        |                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------+--------------------------------------+
      | Installation Mode                 | Option: **CLI**.                                                                                   | CLI                                  |
      |                                   |                                                                                                    |                                      |
      |                                   | You need to remotely log in to the server to run the installation command provided on the console. |                                      |
      +-----------------------------------+----------------------------------------------------------------------------------------------------+--------------------------------------+
      | OS                                | Options: **Linux** and **Windows**. Select **Linux** in this example.                              | Linux                                |
      +-----------------------------------+----------------------------------------------------------------------------------------------------+--------------------------------------+
      | UniAgent Version                  | Select a UniAgent version. The latest version is selected by default.                              | Latest version                       |
      +-----------------------------------+----------------------------------------------------------------------------------------------------+--------------------------------------+
      | Copy and Run Installation Command | Click **Copy** to copy the installation command.                                                   | Copy the Linux installation command. |
      +-----------------------------------+----------------------------------------------------------------------------------------------------+--------------------------------------+

#. Log in to the ECS and run the Linux installation command copied in :ref:`6 <aom_00_0007__en-us_topic_0000001944840874_en-us_topic_0000001860836318_li208691737122816>` as the **root** user.

#. Check the UniAgent status in the UniAgent list. If the UniAgent status is **Running**, the installation is successful.

.. _aom_00_0007__en-us_topic_0000001988246261_en-us_topic_0000001118763740_section665755611241:

Creating a Host Group
---------------------

You can create host groups of the IP address and custom identifier types. In this example, select the IP address type.

#. Log in to the AOM 2.0 console.
#. In the navigation pane, choose **Settings** > **Global Settings**.
#. On the **Global Settings** page, choose **Collection Settings** > **Host Groups** and click **Create Host Group**.
#. On the displayed page, set related parameters.

   .. table:: **Table 2** Parameters

      +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | Parameter       | Description                                                                                                                                                                                     | Example |
      +=================+=================================================================================================================================================================================================+=========+
      | Host Group      | Name of a host group. Enter 1 to 64 characters. Do not start with a period (.) or underscore (_) or end with a period. Only letters, digits, hyphens (-), underscores, and periods are allowed. | aom-ecs |
      +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | Host Group Type | Type of the host group. Options: **IP** and **Custom identifier**. In this example, select **IP**.                                                                                              | IP      |
      +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | Host Type       | Host type. Default: **Linux**.                                                                                                                                                                  | Linux   |
      +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+
      | Remark          | Host group remarks. Enter up to 1,024 characters. In this example, leave this parameter blank.                                                                                                  | ``-``   |
      +-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+---------+

#. In the host list, select one or more hosts to add to the group and click **OK**.

.. _aom_00_0007__section1867918161483:

Connecting an ECS to AOM
------------------------

#. Log in to the AOM 2.0 console.
#. In the navigation pane, choose **Access Center** > **Access Center**. Click **Try New Version** in the upper right corner of the page.
#. Locate the **Elastic Cloud Server (ECS)** card under **Running environments** and click **Ingest Metric (AOM)** on the card.
#. Set parameters for connecting to the ECS.

   a. Select a Prometheus instance.

      #. Instance Type: Select a Prometheus instance type. Options: **Prometheus for ECS** and **Common Prometheus instance**.

      #. .. _aom_00_0007__en-us_topic_0000001971665332_li11732131215142:

         **Instance Name**: Select a Prometheus instance from the drop-down list. If no Prometheus instance is available, click **Create Instance**. For details, see :ref:`Table 3 <aom_00_0007__table1085351216573>`.

         .. _aom_00_0007__table1085351216573:

         .. table:: **Table 3** Creating a Prometheus instance

            +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
            | Parameter             | Description                                                                                                                                                 | Example               |
            +=======================+=============================================================================================================================================================+=======================+
            | Instance Name         | Prometheus instance name.                                                                                                                                   | mon_ECS               |
            |                       |                                                                                                                                                             |                       |
            |                       | Enter a maximum of 100 characters and do not start or end with an underscore (_) or hyphen (-). Only letters, digits, underscores, and hyphens are allowed. |                       |
            +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
            | Enterprise project.   | Select the required enterprise project. The default value is **default**.                                                                                   | default               |
            |                       |                                                                                                                                                             |                       |
            |                       | -  If you have selected **All** for **Enterprise Project** on the global settings page, select one from the drop-down list here.                            |                       |
            |                       | -  If you have already selected an enterprise project on the global settings page, this option will be grayed and cannot be changed.                        |                       |
            +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
            | Instance Type         | Type of the Prometheus instance. Options: **Prometheus for ECS** and **Common Prometheus instance**.                                                        | Prometheus for ECS    |
            +-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

   b. Select a host group.

      In the host group list, select the host group created in :ref:`Creating a Host Group <aom_00_0007__en-us_topic_0000001988246261_en-us_topic_0000001118763740_section665755611241>`.

   c. Configure the collection.

      Under **Configure Collection**, set parameters by referring to the following table.

      .. table:: **Table 4** Collection configuration

         +------------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
         | Category               | Parameter                      | Description                                                                                                                                                                                                   | Example         |
         +========================+================================+===============================================================================================================================================================================================================+=================+
         | Basic Settings         | Configuration Name             | Name of a metric ingestion rule.                                                                                                                                                                              | ecs-rule        |
         |                        |                                |                                                                                                                                                                                                               |                 |
         |                        |                                | Enter up to 50 characters starting with a letter. Only letters, digits, underscores (_), and hyphens (-) are allowed.                                                                                         |                 |
         +------------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
         | Metric Collection Rule | Metric Collection Interval (s) | Interval for collecting metrics, in seconds. Options: **10**, **30**, and **60** (default).                                                                                                                   | 60              |
         +------------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
         |                        | Metric Collection Timeout (s)  | Timeout period for executing a metric collection task, in seconds. Options: **10**, **30**, and **60** (default). **The timeout period cannot exceed the collection interval.**                               | 60              |
         +------------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
         |                        | Executor                       | User who executes the metric ingestion rule, that is, the user of the selected host group. Default: **root**.                                                                                                 | root            |
         +------------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
         | Other                  | Custom Dimensions              | Dimensions (key-value pairs) added to specify additional metric attributes. You can click **Add Dimension** to add multiple custom dimensions (key-value pairs). In this example, leave this parameter blank. | ``-``           |
         +------------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+
         |                        | Import ECS Tags as Dimensions  | This function is disabled by default. If it is enabled, ECS tags (key-value pairs) will be written to metric dimensions and tag changes will be synchronized to AOM.                                          | Disable         |
         +------------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------+

#. After the configuration is complete, click **Next**. The ECS metrics can then be ingested.

.. _aom_00_0007__section51417537472:

Setting a Metric Alarm Rule
---------------------------

Metric alarm rules can be created in the following modes: **Select from all metrics** and **PromQL**.

The following describes how to create an alarm rule when **Configuration Mode** is set to **Select from all metrics**.

#. In the navigation pane, choose **Alarm Center** > **Alarm Rules**. Then, click **Create Alarm Rule**.

#. Set basic information about the alarm rule by referring to :ref:`Table 5 <aom_00_0007__en-us_topic_0000001582534348_table1730711167518>`.

   .. _aom_00_0007__en-us_topic_0000001582534348_table1730711167518:

   .. table:: **Table 5** Basic information

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                                | Example               |
      +=======================+============================================================================================================================================================================+=======================+
      | Original Rule Name    | Name of a rule. Enter a maximum of 256 characters and do not start or end with underscores (_) or hyphens (-). Only letters, digits, underscores, and hyphens are allowed. | monitor_ecs           |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Rule Name             | Name of a rule. Enter a maximum of 256 characters and do not start or end with underscores (_) or hyphens (-). Only letters, digits, underscores, and hyphens are allowed. | ``-``                 |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Enterprise Project    | Select the required enterprise project. The default value is **default**.                                                                                                  | default               |
      |                       |                                                                                                                                                                            |                       |
      |                       | -  If you have selected **All** for **Enterprise Project** on the global settings page, select one from the drop-down list here.                                           |                       |
      |                       | -  If you have already selected an enterprise project on the global settings page, this option will be grayed and cannot be changed.                                       |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Description           | Description of the rule. Enter up to 1,024 characters. In this example, leave this parameter blank.                                                                        | ``-``                 |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Set the detailed information about the alarm rule.

   a. **Rule Type**: **Metric alarm rule**.

   b. **Configuration Mode**: **Select from all metrics**. Then you can set alarm conditions for different types of resources.

   c. Select the target Prometheus instance from the drop-down list. In this example, select the instance created in :ref:`4.a.ii <aom_00_0007__en-us_topic_0000001971665332_li11732131215142>`.

   d. Set alarm rule details. :ref:`Table 6 <aom_00_0007__aom_00_0008_en-us_topic_0000001582534348_table8512161614337>` describes the parameters.

      After the setting is complete, the monitored metric data is displayed in a line graph above the alarm conditions. You can click **Add Metric** to add more metrics and set the statistical period and detection rules for them.

      .. _aom_00_0007__aom_00_0008_en-us_topic_0000001582534348_table8512161614337:

      .. table:: **Table 6** Alarm rule details

         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Parameter             | Description                                                                                                                                                                                                      | Example               |
         +=======================+==================================================================================================================================================================================================================+=======================+
         | Multiple Metrics      | Calculation is performed based on the preset alarm conditions one by one. An alarm is triggered when one of the conditions is met.                                                                               | Multiple Metrics      |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Metric                | Metric to be monitored. Click the **Metric** text box. In the resource tree on the right, select a target metric by resource type.                                                                               | node_network_up       |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Statistical Period    | Interval at which metric data is collected.                                                                                                                                                                      | 1 minute              |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Conditions            | Metric monitoring scope. If this parameter is left blank, all resources are covered. In this example, leave this parameter blank.                                                                                | ``-``                 |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Grouping Condition    | Aggregate metric data by the specified field and calculate the aggregation result.                                                                                                                               | Not grouped           |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Rule                  | Detection rule of a metric alarm, which consists of the statistical mode (**Avg**, **Min**, **Max**, **Sum**, and **Samples**), determination criterion (**>=**, **<=**, **>**, and **<**), and threshold value. | **Avg > 1**           |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Trigger Condition     | When the metric value meets the alarm condition for a specified number of consecutive periods, a metric alarm will be generated.                                                                                 | 3                     |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Alarm Severity        | Severity of a metric alarm.                                                                                                                                                                                      | |image5|              |
         |                       |                                                                                                                                                                                                                  |                       |
         |                       | -  |image1|: a critical alarm.                                                                                                                                                                                   |                       |
         |                       | -  |image2|: a major alarm.                                                                                                                                                                                      |                       |
         |                       | -  |image3|: a minor alarm.                                                                                                                                                                                      |                       |
         |                       | -  |image4|: a warning.                                                                                                                                                                                          |                       |
         +-----------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **Advanced Settings** and set information such as **Check Interval** and **Alarm Clearance**. For details about the parameters, see :ref:`Table 7 <aom_00_0007__aom_00_0008_en-us_topic_0000001582534348_table55151160338>`.

   .. _aom_00_0007__aom_00_0008_en-us_topic_0000001582534348_table55151160338:

   .. table:: **Table 7** Advanced settings

      +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                          | Description                                                                                                                                                                                                                             | Example                                                                                                                           |
      +====================================+=========================================================================================================================================================================================================================================+===================================================================================================================================+
      | Check Interval                     | Interval at which metric query and analysis results are checked.                                                                                                                                                                        | Custom interval: 1 minute                                                                                                         |
      +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Alarm Clearance                    | The alarm will be cleared when the alarm condition is not met for a specified number of consecutive periods.                                                                                                                            | 1                                                                                                                                 |
      +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Action Taken for Insufficient Data | Action to be taken if there is no or insufficient metric data within the monitoring period. Enable this option if needed.                                                                                                               | Enabled: If the data is insufficient for **1** period, the status will change to **Insufficient data** and an alarm will be sent. |
      +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Tags                               | Click |image6| to add an alarm rule tag. It is an alarm identification attribute in the format of "key:value". It is used in alarm noise reduction scenarios. In this example, leave this parameter blank.                              | ``-``                                                                                                                             |
      |                                    |                                                                                                                                                                                                                                         |                                                                                                                                   |
      |                                    | For details, see :ref:`Alarm Tags and Annotations <mon_01_0044>`.                                                                                                                                                                       |                                                                                                                                   |
      +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+
      | Annotations                        | Click |image7| to add an alarm rule annotation. It is an alarm non-identification attribute in the format of "key:value". It is used in alarm notification and message template scenarios. In this example, leave this parameter blank. | ``-``                                                                                                                             |
      |                                    |                                                                                                                                                                                                                                         |                                                                                                                                   |
      |                                    | For details, see :ref:`Alarm Tags and Annotations <mon_01_0044>`.                                                                                                                                                                       |                                                                                                                                   |
      +------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------+

#. Set an alarm notification policy. For details, see :ref:`Table 8 <aom_00_0007__aom_00_0008_table18775831101314>`.

   .. _aom_00_0007__aom_00_0008_table18775831101314:

   .. table:: **Table 8** Alarm notification policy parameters

      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+
      | Parameter             | Description                                                                                                                                                                                                                                                                                                                                                                                             | Example                                               |
      +=======================+=========================================================================================================================================================================================================================================================================================================================================================================================================+=======================================================+
      | Notify When           | Set the scenario for sending alarm notifications. By default, **Alarm triggered** and **Alarm cleared** are selected.                                                                                                                                                                                                                                                                                   | Retain the default value.                             |
      |                       |                                                                                                                                                                                                                                                                                                                                                                                                         |                                                       |
      |                       | -  **Alarm triggered**: If the alarm trigger condition is met, the system sends an alarm notification to the specified personnel by email or SMS.                                                                                                                                                                                                                                                       |                                                       |
      |                       | -  **Alarm cleared**: If the alarm clearance condition is met, the system sends an alarm notification to the specified personnel by email or SMS.                                                                                                                                                                                                                                                       |                                                       |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+
      | Alarm Mode            | -  **Direct alarm reporting**: An alarm is directly sent when the alarm condition is met. If you select this mode, set an interval for notification and specify whether to enable a notification rule.                                                                                                                                                                                                  | -  **Alarm Mode**: Select **Direct alarm reporting**. |
      |                       | -  **Frequency**: frequency for sending alarm notifications. Select a desire value from the drop-down list.                                                                                                                                                                                                                                                                                             | -  **Frequency**: Select **Once**.                    |
      |                       | -  **Notification Rule**: After the rule is enabled, the system sends notifications based on the associated SMN topic and message template. If there is no alarm notification rule you want to select, click **Add Rule** in the drop-down list to create one. For details about how to set alarm notification rules, see :ref:`Setting an Alarm Notification Rule <aom_00_0003__section291715218147>`. | -  **Notification Rule**: **Mon_aom**                 |
      +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+-------------------------------------------------------+

#. Click **Confirm**. Then click **View Rule** to view the created rule.

   In the expanded list, if a metric value meets the configured alarm condition, a metric alarm is generated on the alarm page. To view the alarm, choose **Alarm Center** > **Alarm List** in the navigation pane. If a metric value meets the preset notification policy, the system sends an alarm notification to the specified personnel by email or SMS.

Related Information
-------------------

After an alarm rule is configured, you can perform the following operations if needed:

-  Choose **Alarm Center** > **Alarm List** to check alarms. For details, see :ref:`Checking AOM Alarms or Events <mon_01_0011>`.
-  Create metric alarm rules in different ways. For details, see :ref:`Creating an AOM Metric Alarm Rule <mon_01_0008>`.

.. |image1| image:: /_static/images/en-us_image_0000002371028345.png
.. |image2| image:: /_static/images/en-us_image_0000002371028397.png
.. |image3| image:: /_static/images/en-us_image_0000002337030080.png
.. |image4| image:: /_static/images/en-us_image_0000002337030096.png
.. |image5| image:: /_static/images/en-us_image_0000002371028381.png
.. |image6| image:: /_static/images/en-us_image_0000002336870276.png
.. |image7| image:: /_static/images/en-us_image_0000002336870336.png
