:original_name: mon_01_0037.html

.. _mon_01_0037:

Using AOM to Monitor Clusters
=============================

Clusters deployed using CCE are monitored. Through cluster monitoring, you can view multiple basic metrics (such as cluster status, CPU usage, memory usage, and node status), and related alarms and events in real time. Based on them, you can monitor cluster statuses and handle risks in a timely manner, ensuring stable cluster running.

Constraints
-----------

-  The host status can be **Normal**, **Abnormal**, **Warning**, **Silent**, or **Deleted**. The running status of a host is displayed as **Abnormal** when the host is faulty due to network failures or host power-off or shut-down, or when a threshold alarm is reported on the host.
-  To use CCE functions on the AOM console, you need to obtain CCE permissions in advance.

Procedure
---------

#. Log in to the AOM 2.0 console.
#. In the navigation pane, choose **Container Insights** > **Cluster Monitoring**.
#. In the upper right corner of the page, set cluster filter criteria.

   a. Set a time range to check the CCE clusters reported. You can use a predefined time label, such as **Last hour** and **Last 6 hours**, or customize a time range. Max.: 30 days.
   b. Set the interval for refreshing information. Click |image1| and select a value from the drop-down list, such as **Refresh manually** or **1 minute auto refresh**.

#. Set search criteria such as the cluster name to filter the target cluster. You can also sort clusters by creation time, CPU usage, or memory usage.

5. Click a cluster to go to its details page. In the navigation pane on the left, monitor cluster running conditions by cluster, on dashboards, or through **Alarm Management**.

   -  View information about nodes, workloads, pods (container groups), and containers by cluster.

      -  In the navigation pane on the left, choose **Insights** > **Node** to view information about all nodes in the cluster in real time, including the status, IP address, pod status, CPU usage, and memory usage.

         -  In the upper part of the node list, filter nodes by node name.
         -  Click |image2| in the upper right corner and select or deselect options as required.
         -  Click a node to view its related resources, alarms, and events, and common system devices such as GPUs and NICs.

            -  On the **Overview** tab page, **Cloud-Native Monitoring (New)** is selected by default. You can view metrics such as CPU, memory, and network. Click **Using ICAgent (Old)** and select a target Prometheus instance from the drop-down list. You can view metrics such as CPU, physical memory, and host status.

               To use cloud-native monitoring, connect your cluster to a Prometheus instance for CCE first. If there is no Prometheus instance for CCE, click **Prometheus Monitoring** to create a Prometheus instance by referring to :ref:`Using Prometheus Monitoring to Monitor CCE Cluster Metrics <mon_01_0073>`. After the instance is created, click its name. On the instance details page, choose **Integration Center** and then connect the CCE cluster.

               Click the time selection box in the upper right corner and select a predefined time label or customize a time range from the drop-down list to view resource information.

               Click |image3| in the upper right corner to obtain the latest resource information in real time.

               Click |image4| in the upper right corner of the page to view resource information in full screen.

            -  On the **Related Resources** tab page, the pod (container group) to which the node belongs is displayed.

      -  In the navigation pane on the left, choose **Insights** > **Workload** to view the status and resource usage of all workloads in the cluster.

         -  In the upper part of the workload list, filter workloads by workload name.
         -  Click |image5| in the upper right corner and select or deselect options as required.
         -  Click a workload to view its related resources, alarms, events, and dashboards.

            -  On the **Overview** tab page, **Cloud-Native Monitoring (New)** is selected by default. You can view metrics such as CPU, memory, and network. Click **Using ICAgent (Old)** and select a target Prometheus instance from the drop-down list. You can view metrics such as CPU, physical memory, and file system.
            -  On the **Related Resources** tab page, the pod (container group) to which the workload belongs is displayed.

      -  In the navigation pane on the left, choose **Insights** > **Pod** to view the status and resource usage of all pods in the cluster.

         -  In the upper part of the container group list, filter container groups by name.
         -  Click |image6| in the upper right corner and select or deselect options as required.
         -  Click a container group to view its related resources, alarms, events, and dashboards.

            -  On the **Overview** tab page, **Cloud-Native Monitoring (New)** is selected by default. You can view metrics such as CPU, memory, and network. Click **Using ICAgent (Old)** and select a target Prometheus instance from the drop-down list. You can view metrics such as CPU, physical memory, and file system.
            -  On the **Related Resources** tab page, view nodes, workloads, and containers by name.

      -  In the navigation pane on the left, choose **Insights** > **Container** to view the status and resource usage of all containers in the cluster.

         -  In the upper part of the container list, filter containers by name.
         -  Click |image7| in the upper right corner and select or deselect options as required.
         -  Click a container to view its related resources, alarms, events, and dashboards. On the **Related Resources** tab page, the container group to which the container belongs is displayed by default. Check nodes, workloads, and container groups by name.

   -  Check the cluster running status through **Alarm Management**.

      -  In the navigation pane on the left, choose **Alarm Management** > **Alarm List** to view alarm details of the cluster. For details, see :ref:`Checking AOM Alarms or Events <mon_01_0011>`.
      -  In the navigation pane on the left, choose **Alarm Management** > **Event List** to view event details of the cluster. For details, see :ref:`Checking AOM Alarms or Events <mon_01_0011>`.
      -  In the navigation pane on the left, choose **Alarm Management** > **Alarm Rules** to view the alarm rules related to the cluster. Modify the alarm rules as required. For details, see :ref:`Managing AOM Alarm Rules <mon_01_0050>`.

   -  In the navigation pane on the left, choose **Dashboard** to view the running status of the current cluster.

      -  A CCE Prometheus instance has been connected:

         Select **Cluster View**, **Pod View**, **Host View**, or **Node View** from the drop-down list to view key metrics such as the CPU usage and physical memory usage.

      -  No CCE Prometheus instance is connected:

         Choose **Prometheus Monitoring** and then add a Prometheus instance. For details, see :ref:`Using Prometheus Monitoring to Monitor CCE Cluster Metrics <mon_01_0073>` After the instance is created, click its name. On the instance details page, choose **Integration Center** and then connect the CCE cluster.

.. |image1| image:: /_static/images/en-us_image_0000002337031804.png
.. |image2| image:: /_static/images/en-us_image_0000002371030161.png
.. |image3| image:: /_static/images/en-us_image_0000002371030165.png
.. |image4| image:: /_static/images/en-us_image_0000002336872064.png
.. |image5| image:: /_static/images/en-us_image_0000002370950009.png
.. |image6| image:: /_static/images/en-us_image_0000002337031808.png
.. |image7| image:: /_static/images/en-us_image_0000002336872072.png
