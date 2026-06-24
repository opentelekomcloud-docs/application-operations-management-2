:original_name: aom_01_0054.html

.. _aom_01_0054:

Application Scenarios
=====================

Maintaining Containers
----------------------

**Pain Points**

Prometheus is ideal for monitoring containers. Since self-built Prometheus is costly for small- and medium-sized enterprises (SMEs) and insufficient for large enterprises, many are turning to hosted Prometheus.

**Solutions**

AOM fully interconnects with the open-source Prometheus ecosystem. With Kubernetes clusters connected to Prometheus, enterprises can monitor performance metrics of hosts and Kubernetes clusters through Grafana dashboards.

-  Collect metrics through kube-prometheus-stack, self-built Kubernetes clusters, ServiceMonitor, and PodMonitor to monitor service data deployed in CCE clusters.
-  Various alarm templates help you quickly detect and locate faults.
