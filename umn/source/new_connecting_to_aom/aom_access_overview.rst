:original_name: mon_01_0196.html

.. _mon_01_0196:

AOM Access Overview
===================

AOM is a unified platform for observability analysis of cloud services. You can quickly ingest AOM metrics and LTS logs through the new access center. After the ingestion is complete, you can view the resource or application running status, metric usage, and LTS logs on the :ref:`Metric Browsing <mon_01_0026>` and :ref:`Log Management <mon_01_0027>` pages.

Constraints
-----------

If the old access center is displayed, click **Try New Version** in the upper right corner.

Ingesting Metrics/Logs to AOM
-----------------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Access Center** > **Access Center**.

#. Click **Try New Version** in the upper right corner of the page. The new access center is displayed.

   The **Recommended** area displays six popular cards. They will be automatically updated to the six cards you have recently used.

#. Set criteria to quickly query the metrics, or logs to be ingested.

   -  Filter: Filter content by data source or type.
   -  Attribute filtering: Click the search box and search for content by keyword, data source, or type. You can also enter a keyword to search.

   .. table:: **Table 1** Access overview

      +-----------------------+-------------------------------------------------+-----------------+---------------------------------------------------------------------------------+
      | Type                  | Monitored Object (Card)                         | Data Source     | Access Mode                                                                     |
      +=======================+=================================================+=================+=================================================================================+
      | Self-built middleware | -  MySQL                                        | Metrics         | :ref:`Connecting Self-Built Middleware to AOM <mon_01_0226>`                    |
      |                       | -  Redis                                        |                 |                                                                                 |
      |                       | -  Kafka                                        |                 |                                                                                 |
      |                       | -  Nginx                                        |                 |                                                                                 |
      |                       | -  MongoDB                                      |                 |                                                                                 |
      |                       | -  Consul                                       |                 |                                                                                 |
      |                       | -  HAProxy                                      |                 |                                                                                 |
      |                       | -  PostgreSQL                                   |                 |                                                                                 |
      |                       | -  Elasticsearch                                |                 |                                                                                 |
      |                       | -  RabbitMQ                                     |                 |                                                                                 |
      +-----------------------+-------------------------------------------------+-----------------+---------------------------------------------------------------------------------+
      | Running environments  | -  Elastic Cloud Server (ECS)                   | Logs/Metrics    | :ref:`Connecting Running Environments to AOM <mon_01_0197>`                     |
      |                       | -  Cloud Container Engine (CCE)                 |                 |                                                                                 |
      +-----------------------+-------------------------------------------------+-----------------+---------------------------------------------------------------------------------+
      | APIs/protocols...     | -  AOM APIs                                     | Logs/Metrics    | :ref:`Ingesting Data to AOM Using Open-Source APIs and Protocols <mon_01_0205>` |
      |                       | -  LTS APIs                                     |                 |                                                                                 |
      |                       | -  Cross-Account Ingestion - Log Stream Mapping |                 |                                                                                 |
      |                       | -  Custom Prometheus Metrics                    |                 |                                                                                 |
      +-----------------------+-------------------------------------------------+-----------------+---------------------------------------------------------------------------------+

#. Hover the pointer over the card and click the blue text to check LTS documents or ingest metrics.

   -  Click **Ingest Metric (AOM)** to quickly ingest metrics.
   -  Click **Ingest Log (LTS)** on **Ingest Log (LTS) Details** to quickly ingest logs or click **Details** to check documents related to log ingestion.
