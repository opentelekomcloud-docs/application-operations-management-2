:original_name: mon_01_0205.html

.. _mon_01_0205:

Ingesting Data to AOM Using Open-Source APIs and Protocols
==========================================================

AOM provides a unified entry for observability analysis of cloud services. Through the access center, you can ingest metrics into AOM using open-source APIs and protocols, ingest traces to APM, and check documents related to log ingestion to LTS.

Procedure
---------

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Access Center** > **Access Center** to go to the new access center.

   If the old access center is displayed, click **Try New Version** in the upper right corner.

#. Select the check box next to **APIs/protocols...** under **Types** to filter out target cards.

#. Click **Ingest Metric (AOM)** to quickly ingest metrics, or click **Ingest Log (LTS) Details** to ingest logs or check documents related to log ingestion.

   -  **Ingest Metric (AOM)**: AOM supports metric ingestion using open-source APIs and protocols. By clicking **Ingest Metric (AOM)**, you can quickly ingest metrics using open-source APIs and protocols.
   -  **Ingest Log (LTS) Details**: AOM provides an entry for ingesting logs to LTS using open-source APIs and protocols.

      -  By clicking **Details** on **Ingest Log (LTS) Details**, you can check documents related to log ingestion. You can ingest logs according to the documents.
      -  For some components, you can quickly ingest their logs by clicking **Ingest Log (LTS)**. For example, the **Cross-Account Ingestion - Log Stream Mapping** card.

   .. table:: **Table 1** Ingesting data to AOM using open-source APIs and protocols

      +----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Card                                         | Related Operation                                                                                                                                                                                                                  |
      +==============================================+====================================================================================================================================================================================================================================+
      | AOM APIs                                     | Use the open APIs of AOM to report metric data. For details, see `Adding Monitoring Data <https://docs.otc.t-systems.com/api/aom/aom_04_0013.html>`__.                                                                             |
      +----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | LTS APIs                                     | Use the open APIs of LTS to report log data. For details, see `Using APIs to Ingest Logs to LTS <https://docs.otc.t-systems.com/usermanual/lts/lts_04_0215.html>`__.                                                               |
      +----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Cross-Account Ingestion - Log Stream Mapping | Create an agency to map the delegator account's log stream to the delegated account's log stream. For details, see `Ingesting Logs to LTS Across IAM Accounts <https://docs.otc.t-systems.com/usermanual/lts/lts_04_1112.html>`__. |
      +----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Custom Prometheus Metrics                    | Ingest custom Prometheus metrics. For details, see :ref:`Ingesting Custom Prometheus Metrics to AOM <mon_01_0205__section41341623144317>`.                                                                                         |
      +----------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. _mon_01_0205__section41341623144317:

Ingesting Custom Prometheus Metrics to AOM
------------------------------------------

You can ingest custom Prometheus metrics. They can be automatically reported to AOM.

-  **Prerequisites**

   -  You have connected a Prometheus instance for ECS or a common Prometheus instance. For details, see :ref:`Managing Prometheus Instances <mon_01_0072>` or :ref:`Connecting Open-Source Monitoring Systems to AOM <mon_01_0070>`.
   -  A host group has been created. For details, see :ref:`(New) Managing Host Groups <agent_02_1033>`.

-  **Procedure**

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Access Center** > **Access Center**. Click **Try New Version** in the upper right corner of the page.

#. Click **Custom Prometheus Metrics** under **APIs/Protocols...**, and then click **Ingest Metric (AOM)** on the card to enter the configuration page.

#. Configure parameters for ingesting custom Prometheus metrics.

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

      .. table:: **Table 2** Parameters for configuring a collection task

         +------------------------+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Operation              | Parameter                      | Description                                                                                                                                                                 |
         +========================+================================+=============================================================================================================================================================================+
         | Basic Settings         | Configuration Name             | Name of a custom metric ingestion rule. Enter 1 to 50 characters starting with a letter. Only letters, digits, underscores (_), and hyphens (-) are allowed.                |
         +------------------------+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Metric Collection Rule | Collection Target              | Enter the target IP address and port number for collecting Prometheus metrics, for example, **10.0.0.1:3306**.                                                              |
         +------------------------+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                        | Metric Collection Interval (s) | Interval for collecting metrics, in seconds. Options: **10**, **30**, and **60** (default).                                                                                 |
         +------------------------+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                        | Metric Collection Timeout (s)  | Timeout period for executing a metric collection task, in seconds. Options: **10**, **30**, and **60** (default). The timeout period cannot exceed the collection interval. |
         +------------------------+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                        | Executor                       | User who executes the metric ingestion rule, that is, the user of the selected host group. By default, the executor is **root**.                                            |
         +------------------------+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Other                  | Custom Dimensions              | Dimensions (key-value pairs) added to specify additional metric attributes. You can click **Add Dimension** to add multiple custom dimensions (key-value pairs).            |
         |                        |                                |                                                                                                                                                                             |
         |                        |                                | -  Key: key of the additional attribute of a metric. Enter 1 to 64 characters starting with a letter or underscore (_). Only letters, digits, and underscores are allowed.  |
         |                        |                                | -  Value: corresponds to the key of the additional attribute of a metric.                                                                                                   |
         |                        |                                |                                                                                                                                                                             |
         |                        |                                | A maximum of 10 custom dimensions can be added. Example: Set the key to **app** and value to **abc**.                                                                       |
         +------------------------+--------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

      After the parameters are configured, you can click **YAML** to view the configuration data in YAML format.

#. After the configuration is complete, click **Next**. The custom Prometheus metrics can then be ingested.

   After ingesting custom Prometheus metrics, you can perform the following operations:

   -  Go to the **Metric Browsing** page to analyze metrics. For details, see :ref:`Observability Metric Browsing <mon_01_0026>`.
   -  Go to the **Access Management** page to view, edit, or delete the configured ingestion rule. For details, see :ref:`Managing Metric and Log Ingestion <mon_01_0206>`.
