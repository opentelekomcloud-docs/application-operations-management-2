:original_name: mon_01_0051.html

.. _mon_01_0051:

AOM Access Overview
===================

AOM monitors metric and log data from multiple dimensions at different layers in multiple scenarios. Through the old access center, you can quickly ingest metrics and logs to monitor. After the ingestion is complete, you can view the metrics, logs, and statuses of related resources or applications on the :ref:`Metric Browsing <mon_01_0026>` page.

Constraints
-----------

If you want to switch from the new access center to the old one, you need to click **Back to Old Version** in the upper right corner.

Ingesting Metrics or Logs to AOM
--------------------------------

#. Log in to the AOM 2.0 console.
#. In the navigation pane, choose **Access Center** > **Access Center**.
#. Ingest metrics or logs based on monitored object types.

   .. table:: **Table 1** Access overview

      +---------------------------------------+-----------------------------------------------------------------------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Type                                  | Monitored Object                                                                        | Data Source     | Access Mode                                                                                                                                                                       |
      +=======================================+=========================================================================================+=================+===================================================================================================================================================================================+
      | Prometheus running environment access | Cloud Container Engine (CCE) (ICAgent)                                                  | Metrics         | Uses ICAgent to collect CCE cluster metrics. By default, ICAgent is installed when you purchase a CCE cluster and node. ICAgent automatically reports CCE cluster metrics to AOM. |
      |                                       |                                                                                         |                 |                                                                                                                                                                                   |
      |                                       |                                                                                         |                 | For details about the CCE cluster metrics that are automatically reported to AOM, see :ref:`Basic Metrics: VM Metrics <aom_01_0022>`.                                             |
      +---------------------------------------+-----------------------------------------------------------------------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Prometheus cloud service access       | Supported cloud services                                                                | Metrics         | :ref:`Connecting Cloud Services to AOM <mon_01_0067>`                                                                                                                             |
      +---------------------------------------+-----------------------------------------------------------------------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Open-source monitoring system access  | Common Prometheus instance                                                              | Metrics         | :ref:`Connecting Open-Source Monitoring Systems to AOM <mon_01_0070>`                                                                                                             |
      +---------------------------------------+-----------------------------------------------------------------------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Prometheus API/SDK access             | AOM APIs                                                                                | Metrics         | Through `APIs <https://docs.otc.t-systems.com/api/aom/aom_04_0013.html>`__                                                                                                        |
      +---------------------------------------+-----------------------------------------------------------------------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Custom Prometheus plug-in access      | Custom Prometheus plug-ins                                                              | Metrics         | :ref:`Connecting Custom Plug-ins to AOM <agent_01_00272>`                                                                                                                         |
      +---------------------------------------+-----------------------------------------------------------------------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Log ingestion                         | Cloud services, self-built software, APIs/SDKs, and cross-account ingestion-log streams | Logs            | `Log Ingestion <https://docs.otc.t-systems.com/usermanual/lts/lts_02_0030.html>`__                                                                                                |
      +---------------------------------------+-----------------------------------------------------------------------------------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
