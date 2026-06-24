:original_name: mon_01_0197.html

.. _mon_01_0197:

Connecting Running Environments to AOM
======================================

AOM provides a unified entry for observability analysis of cloud services. Through the access center, you can ingest the metrics of running environments (such as ECS and CCE) to AOM and check documents related to log ingestion.

Procedure
---------

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Access Center** > **Access Center** to go to the new access center.

   If the old access center is displayed, click **Try New Version** in the upper right corner.

#. Select the check box next to **Running environments** under **Types** to filter out the running environment cards.

#. Click **Ingest Metric (AOM)** to quickly ingest metrics or click **Ingest Log (LTS) Details** to check documents related to log ingestion.

   -  **Ingest Metric (AOM)**: AOM supports metric ingestion for running environments. By clicking **Ingest Metric (AOM)**, you can quickly ingest metrics of running environments.
   -  **Ingest Log (LTS) Details**: AOM provides an entry for ingesting logs of running environments to LTS.

      -  By clicking **Details** on **Ingest Log (LTS) Details**, you can check the documents related to log ingestion. You can ingest logs according to the documents.
      -  By clicking **Ingest Log (LTS)** on **Ingest Log (LTS) Details**, you can quickly ingest logs of running environments.

   .. table:: **Table 1** Connecting running environments to AOM

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Card                              | Related Operation                                                                                                                                                                                                                                                                                 |
      +===================================+===================================================================================================================================================================================================================================================================================================+
      | Elastic Cloud Server (ECS)        | ECS is a cloud server that allows on-demand allocation and elastic computing capability scaling. It helps you build a reliable, secure, flexible, and efficient application environment to ensure that your services can run stably and continuously, improving O&M efficiency. For details, see: |
      |                                   |                                                                                                                                                                                                                                                                                                   |
      |                                   | -  `Ingesting ECS Text Logs to LTS <https://docs.otc.t-systems.com/usermanual/lts/lts_04_1031.html>`__.                                                                                                                                                                                           |
      |                                   | -  :ref:`Ingesting ECS Metrics (AOM) <mon_01_0197__section160594303515>`                                                                                                                                                                                                                          |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cloud Container Engine (CCE)      | CCE is a high-performance, high-reliability service through which enterprises can manage containerized applications. CCE supports native Kubernetes applications and tools, allowing you to easily establish a container runtime environment on the cloud. For details, see:                      |
      |                                   |                                                                                                                                                                                                                                                                                                   |
      |                                   | -  CCE metric ingestion to AOM: By default, ICAgents are installed on CCE clusters upon your purchase. CCE cluster metrics will be automatically reported to AOM.                                                                                                                                 |
      |                                   | -  `Ingesting CCE Application Logs to LTS <https://docs.otc.t-systems.com/usermanual/lts/lts_04_0511.html>`__                                                                                                                                                                                     |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _mon_01_0197__section160594303515:

Connecting an ECS to AOM
------------------------

Node Exporter is an open-source metric collection plug-in from Prometheus. It collects different types of data from target jobs and converts them into the time series data supported by Prometheus. Connect an ECS to AOM. Then you can install Node Exporter and configure collection tasks for the host group. The collected metrics will be stored in the Prometheus instance for ECS for easy management.

**Constraints**

A host supports only one Node Exporter.

**Prerequisites**

-  You have connected a Prometheus instance for ECS or a common Prometheus instance. For details, see :ref:`Managing Prometheus Instances <mon_01_0072>` or :ref:`Connecting Open-Source Monitoring Systems to AOM <mon_01_0070>`.
-  A host group has been created. For details, see :ref:`(New) Managing Host Groups <agent_02_1033>`.

**Procedure**

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Access Center** > **Access Center**. Click **Try New Version** in the upper right corner of the page.

#. Locate the **Elastic Cloud Server (ECS)** card under **Running environments** and click **Ingest Metric (AOM)** on the card.

#. Set parameters for connecting to the ECS.

   a. Select a Prometheus instance.

      #. **Instance Type**: Select a Prometheus instance type. Options: **Prometheus for ECS** and **Common Prometheus instance**.

      #. **Instance Name**: Select a Prometheus instance from the drop-down list.

         If no Prometheus instance is available, click :ref:`Create Instance <mon_01_0072>` to create one.

   b. Select a host group.

      In the host group list, select a target host group.

      -  If no host group is available, click :ref:`Create Host Group <uiagent_01_0020>` to create one.
      -  You can also perform editing, deletion, and other operations on the host group as needed. For details, see :ref:`(New) Managing Host Groups <uiagent_02_1033>`.

      Collection configurations are delivered by host group. Therefore, it is easy for you to configure data collection for multiple hosts. When there is a new host, simply add it to a host group and the host will automatically inherit the log ingestion configurations associated with the host group.

   c. Configure the collection.

      Under **Configure Collection**, set parameters by referring to the following table.

      .. table:: **Table 2** Collection configuration

         +------------------------+--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Category               | Parameter                      | Description                                                                                                                                                                                                                               |
         +========================+================================+===========================================================================================================================================================================================================================================+
         | Basic Settings         | Configuration Name             | Name of a custom metric ingestion rule. Enter 1 to 50 characters starting with a letter. Only letters, digits, underscores (_), and hyphens (-) are allowed.                                                                              |
         +------------------------+--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Metric Collection Rule | Metric Collection Interval (s) | Interval for collecting metrics, in seconds. Options: **10**, **30**, and **60** (default).                                                                                                                                               |
         +------------------------+--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                        | Metric Collection Timeout (s)  | Timeout period for executing a metric collection task, in seconds. Options: **10**, **30**, and **60** (default). **The timeout period cannot exceed the collection interval.**                                                           |
         +------------------------+--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                        | Executor                       | User who executes the metric ingestion rule, that is, the user of the selected host group. Default: **root**.                                                                                                                             |
         +------------------------+--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Other                  | Custom Dimensions              | Dimensions (key-value pairs) added to specify additional metric attributes. You can click **Add Dimension** to add multiple custom dimensions (key-value pairs).                                                                          |
         |                        |                                |                                                                                                                                                                                                                                           |
         |                        |                                | -  Key: key of the additional attribute of a metric. Enter 1 to 64 characters starting with a letter or underscore (_). Only letters, digits, and underscores are allowed.                                                                |
         |                        |                                | -  Value: corresponds to the key of the additional attribute of a metric.                                                                                                                                                                 |
         |                        |                                |                                                                                                                                                                                                                                           |
         |                        |                                | Up to 10 dimensions can be added. Example: Set the key to **app** and value to **abc**.                                                                                                                                                   |
         +------------------------+--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                        | Import ECS Tags as Dimensions  | Whether to import ECS tags as dimensions.                                                                                                                                                                                                 |
         |                        |                                |                                                                                                                                                                                                                                           |
         |                        |                                | -  **Disable**: AOM does not write ECS tags (key-value pairs) into metric dimensions. ECS tag changes (such as addition, deletion, and modification) will not be synchronized to metric dimensions. This function is disabled by default. |
         |                        |                                |                                                                                                                                                                                                                                           |
         |                        |                                | -  **Enable**: AOM writes ECS tags (key-value pairs) into metric dimensions.                                                                                                                                                              |
         |                        |                                |                                                                                                                                                                                                                                           |
         |                        |                                |    ECS tag changes (such as addition, deletion, and modification) will be synchronized to metric dimensions.                                                                                                                              |
         +------------------------+--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. After the configuration is complete, click **Next**. The ECS is then connected.

   After connecting to the ECS, perform the following operations if needed:

   -  Go to the **Metric Browsing** page to analyze metrics. For details, see :ref:`Observability Metric Browsing <mon_01_0026>`.
   -  Go to the **Access Management** page to view, edit, or delete the configured ingestion rule. For details, see :ref:`Managing Metric and Log Ingestion <mon_01_0206>`.

   -  Go to the **Infrastructure Monitoring** > **Host Monitoring** page to view host monitoring information. For details, see :ref:`Host Monitoring <mon_01_0038>`.
