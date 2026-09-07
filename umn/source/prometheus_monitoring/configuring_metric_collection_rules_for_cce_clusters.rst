:original_name: mon_01_0081.html

.. _mon_01_0081:

Configuring Metric Collection Rules for CCE Clusters
====================================================

By adding ServiceMonitor or PodMonitor, you can configure metric collection rules to monitor the applications deployed in CCE clusters.

Prerequisite
------------

Both your service and CCE cluster have been connected to a Prometheus instance for CCE. For details, see :ref:`Using Prometheus Monitoring to Monitor CCE Cluster Metrics <mon_01_0073>`.

Constraints
-----------

Only when kube-prometheus-stack installed on the **Add-ons** page of CCE or the **Integration Center** page of the Prometheus instance for CCE on AOM is 3.9.0 or later and is still running, can you enable or disable collection rules.

To view the kube-prometheus-stack status, log in to the CCE console and access the cluster page, choose **Add-ons** in the navigation pane, and locate that add-on on the right.

Adding ServiceMonitor
---------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Prometheus Monitoring** > **Instances**.

#. In the instance list, click a Prometheus instance for CCE.

#. In the navigation pane on the left, choose **Metric Management**. On the **Settings** tab page, click **ServiceMonitor**.

#. Click **Add ServiceMonitor**. In the displayed dialog box, set related parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002337031540.png
      :alt: **Figure 1** Adding ServiceMonitor

      **Figure 1** Adding ServiceMonitor

   After the configuration is complete, the new collection rule is displayed in the list.

Adding PodMonitor
-----------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Prometheus Monitoring** > **Instances**.

#. In the instance list, click a Prometheus instance for CCE.

#. In the navigation pane on the left, choose **Metric Management**. On the **Settings** tab page, click **PodMonitor**.

#. Click **Add PodMonitor**. In the displayed dialog box, set related parameters and click **OK**.


   .. figure:: /_static/images/en-us_image_0000002337031556.png
      :alt: **Figure 2** Adding PodMonitor

      **Figure 2** Adding PodMonitor

   After the configuration is complete, the new collection rule is displayed in the list.

Other Operations
----------------

Perform the operations listed in :ref:`Table 1 <mon_01_0081__en-us_topic_0169698339_table15831736105910>` if needed.

.. _mon_01_0081__en-us_topic_0169698339_table15831736105910:

.. table:: **Table 1** Related operations

   +-----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Operation                               | Description                                                                                                                                                              |
   +=========================================+==========================================================================================================================================================================+
   | Viewing a metric                        | -  In the list, view information such as the name, tag, namespace, and configuration mode. You can filter information by cluster name, namespace, or configuration mode. |
   |                                         | -  Click |image1| in the **Operation** column. In the displayed dialog box, view details about the ServiceMonitor or PodMonitor collection rule.                         |
   +-----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Enabling or disabling a collection rule | On the **Metric Management** > **Settings** page, click |image2| in the **Status** column to enable or disable a collection rule.                                        |
   +-----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Deleting a metric                       | Click |image3| in the **Operation** column to delete a metric.                                                                                                           |
   +-----------------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002371029921.png
.. |image2| image:: /_static/images/en-us_image_0000002337031536.png
.. |image3| image:: /_static/images/en-us_image_0000002371029913.png
