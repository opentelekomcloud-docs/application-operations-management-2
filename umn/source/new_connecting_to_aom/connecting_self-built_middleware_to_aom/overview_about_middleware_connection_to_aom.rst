:original_name: mon_01_0227.html

.. _mon_01_0227:

Overview About Middleware Connection to AOM
===========================================

AOM provides a unified entry for observability analysis of cloud services. Through the access center, you can ingest the metrics of self-built middleware such as MySQL, Redis, and Kafka into AOM, and check documents related to log ingestion.

Procedure
---------

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Access Center** > **Access Center** to go to the new access center.

   If the old access center is displayed, click **Try New Version** in the upper right corner.

#. Select **Self-built middleware** under **Types** to filter out your target middleware card.

#. Click **Ingest Metric (AOM)** to quickly ingest middleware metrics to AOM.

   -  **Ingest Metric (AOM)**: AOM enables quick installation and configuration for :ref:`self-built middleware <mon_01_0227__table18680937123916>`. By creating collection tasks and executing plug-in scripts, Prometheus monitoring can monitor reported middleware metrics. It works with AOM and open-source Grafana to provide one-stop, comprehensive monitoring, helping you quickly detect and locate faults and reduce their impact on services. For details about the metrics that can be monitored by AOM, see `open-source Exporters <https://prometheus.io/docs/instrumenting/exporters/>`__.

      To quickly ingest middleware metrics to AOM, perform the following steps:

      a. Install UniAgent on your VM for installing Exporters and creating collection tasks. For details, see :ref:`(New) Installing UniAgents <uiagent_02_0005>`.
      b. Create a Prometheus instance for ECS or a common Prometheus instance and associate it with a collection task to mark and categorize collected data. For details, see :ref:`Managing Prometheus Instances <mon_01_0072>`.
      c. Connect middleware to AOM. For details, see :ref:`Ingesting MySQL Metrics to AOM <mon_01_0213>`.
      d. After middleware is connected to AOM, their metrics can be reported to AOM. You can go to the :ref:`Metric Browsing <mon_01_0026>` page to query metrics.

   .. _mon_01_0227__table18680937123916:

   .. table:: **Table 1** Connecting self-built middleware to AOM

      +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Card          | Related Operation                                                                                                                                                                                                           |
      +===============+=============================================================================================================================================================================================================================+
      | MySQL         | A stable, efficient relational database for heavy data volumes. Used for website and application development. For details, see: :ref:`Ingesting MySQL Metrics to AOM <mon_01_0213>`.                                        |
      +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Redis         | In-memory storage system for multiple data structure types. Used as a database, cache, and message broker. For details, see: :ref:`Ingesting Redis Metrics to AOM <mon_01_0214>`.                                           |
      +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Kafka         | Distributed stream processing platform with high throughput and low latency. Used for real-time data processing and log aggregation. For details, see: :ref:`Ingesting Kafka Metrics to AOM <mon_01_0215>`.                 |
      +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Nginx         | A high-performance HTTP/reverse proxy server for 50,000 concurrent requests. Reduces memory consumption. For details, see: :ref:`Ingesting Nginx Metrics to AOM <mon_01_0216>`.                                             |
      +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | MongoDB       | High-performance, open-source NoSQL database for document storage and flexible data models. For details, see :ref:`Ingesting MongoDB Metrics to AOM <mon_01_0217>`.                                                         |
      +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Consul        | Open-source distributed service discovery and configuration management, supporting multiple data centers and strong consistency. For details, see :ref:`Ingesting Consul Metrics to AOM <mon_01_0218>`.                     |
      +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | HAProxy       | High-performance TCP/HTTP reverse proxy load balancer with high concurrency and flexible configuration for high service availability. For details, see :ref:`Ingesting HAProxy Metrics to AOM <mon_01_0219>`.               |
      +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | PostgreSQL    | A powerful, open source object-relational database system for complex queries and customization. For details, see :ref:`Ingesting PostgreSQL Metrics to AOM <mon_01_0220>`.                                                 |
      +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Elasticsearch | Distributed full-text search engine with PB-level data storage and real-time retrieval. Used for full-text search, analysis, and monitoring. For details, see: :ref:`Ingesting Elasticsearch Metrics to AOM <mon_01_0221>`. |
      +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | RabbitMQ      | Collect RabbitMQ monitoring data. For details, see :ref:`Ingesting RabbitMQ Metrics to AOM <mon_01_0222>`.                                                                                                                  |
      +---------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
