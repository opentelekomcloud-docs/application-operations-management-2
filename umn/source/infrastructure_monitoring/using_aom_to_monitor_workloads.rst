:original_name: mon_01_0025.html

.. _mon_01_0025:

Using AOM to Monitor Workloads
==============================

Workload monitoring is for CCE workloads. It enables you to monitor the resource usage, status, and alarms of workloads in a timely manner so that you can quickly handle alarms or events to ensure smooth workload running. Workloads are classified into Deployments, StatefulSets, DaemonSets, Jobs, and Pods.

Function Introduction
---------------------

-  The workload monitoring solution is ready-to-use. After AOM is enabled, the workload status, CPU usage, and physical memory usage of CCE are displayed on the workload monitoring page by default.

-  For customer-built Kubernetes containers, only Prometheus remote write is supported. After container metrics are written into AOM's metric library, you can query metric data by following instructions listed in :ref:`Observability Metric Browsing <mon_01_0026>`.

-  Workload monitoring adopts the layer-by-layer drill-down design. The hierarchy is as follows: workload > Pod instance > container > process. You can view their relationships on the UI. Metrics and alarms are monitored at each layer.

Procedure
---------

#. Log in to the AOM 2.0 console.
#. In the navigation pane, choose **Infrastructure Monitoring** > **Container Insights** > **Workloads**.
#. In the upper right corner of the page, set filter criteria.

   a. .. _mon_01_0025__li108291342820:

      Set a time range to check the workloads reported. You can use a predefined time label, such as **Last hour** and **Last 6 hours**, or customize a time range. Max.: 30 days.

   b. Set the interval for refreshing information. Click |image1| and select a value from the drop-down list, such as **Refresh manually** or **1 minute auto refresh**.

#. Click any workload tab to view information, such as workload name, status, cluster, and namespace.

   -  In the upper part of the workload list, filter workloads by cluster or namespace.

      To query namespaces, IAM users with the **AOM ReadOnlyAccess** permission need to log in to the CCE console, choose **Permissions** in the navigation pane, and click **Add Permission** in the upper right corner of the page to add required permissions. For CCE namespaces, users or user groups should be granted with read-only (view) or custom permissions. If custom permissions are granted, the list operation permission must be included and namespace resources must also be specified.

   -  Click |image2| in the upper right corner to obtain the latest workload information within the time range specified in :ref:`3.a <mon_01_0025__li108291342820>`.

   -  Click |image3| in the upper right corner and select or deselect columns to display.

   -  Click the name of a workload to view its details.

      -  On the **Pods** tab page, view the all pod conditions of the workload. Click a pod name to view the resource usage and health status of the pod's containers.
      -  On the **Monitoring Views** tab page, view the resource usage of the workload.
      -  On the **Logs** tab page, view the raw and real-time logs of the workload and analyze them as required.
      -  On the **Alarms** tab page, view the alarm details of the workload. For details, see :ref:`Checking AOM Alarms or Events <mon_01_0011>`.
      -  On the **Events** tab page, view the event details of the workload. For details, see :ref:`Checking AOM Alarms or Events <mon_01_0011>`.

.. |image1| image:: /_static/images/en-us_image_0000002337030896.png
.. |image2| image:: /_static/images/en-us_image_0000002371029229.png
.. |image3| image:: /_static/images/en-us_image_0000002370949105.png
