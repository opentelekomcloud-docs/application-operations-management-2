:original_name: mon_01_0080.html

.. _mon_01_0080:

Managing Prometheus Instance Metrics
====================================

You can check the metrics of a default/common Prometheus instance, or a Prometheus instance for CCE/ECS/cloud services, and add/discard metrics.

Prerequisites
-------------

Your service has been connected for Prometheus monitoring. For details, see :ref:`Managing Prometheus Instances <mon_01_0072>`.

Constraints
-----------

-  Only the default/common Prometheus instance, and Prometheus instance for CCE/ECS/cloud services support the functions of checking/adding/discarding metrics.

-  On the **Metric Management** page, you can query only the metrics reported in the last three hours.

-  Default Prometheus instance: Metrics whose names start with **aom\_** or **apm\_** cannot be discarded.

-  Prometheus instances for ECS: Only the metrics collected through collection tasks delivered by UniAgent can be displayed.

-  Prometheus instances for CCE:

   Only the metrics reported by kube-prometheus-stack (later than 3.9.0) installed on CCE **Add-ons** or AOM Prometheus instance for CCE **Integration Center** can be discarded. Ensure that this add-on is running when discarding metrics.

   To view the kube-prometheus-stack status, log in to the CCE console and access the cluster page, choose **Add-ons** in the navigation pane, and locate that add-on on the right.

Viewing Prometheus Instance Metrics
-----------------------------------

Only the default/common Prometheus instance, and Prometheus instance for CCE/ECS/cloud services support the functions of checking metrics.

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, choose **Prometheus Monitoring** > **Instances**.
#. In the instance list, click a desired Prometheus instance. The instance details page is displayed.
#. In the navigation pane on the left, choose **Metric Management**. On the **Metrics** tab page, view the metric names and types of the current Prometheus instance.

   -  Prometheus instance for CCE: You can filter metrics by cluster name, job name, or metric type, or enter a metric name keyword for fuzzy search.
   -  Prometheus instance for cloud services: You can filter metrics by metric type, or enter a metric name keyword for fuzzy search.
   -  Prometheus instance for ECS: You can filter metrics by metric type, plug-in type, or collection task, or enter a metric name keyword for fuzzy search.
   -  Default Prometheus instance: You can filter metrics by metric type, or enter a metric name keyword for fuzzy search.
   -  Common Prometheus instance: You can filter metrics by metric type, or enter a metric name keyword for fuzzy search.

   .. table:: **Table 1** Metric parameters

      +-----------------------------------+------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                  |
      +===================================+==============================================================================+
      | Metric Name                       | Name of a metric.                                                            |
      +-----------------------------------+------------------------------------------------------------------------------+
      | Metric Type                       | Type of a metric. Options: **Basic metric** and **Custom metric**.           |
      +-----------------------------------+------------------------------------------------------------------------------+
      | Metrics in Last 10 Min            | Number of metrics that are stored in the last 10 minutes.                    |
      |                                   |                                                                              |
      |                                   | This parameter is not supported for Prometheus instances for cloud services. |
      +-----------------------------------+------------------------------------------------------------------------------+
      | Proportion                        | Number of a certain type of metrics/Total number of metrics                  |
      |                                   |                                                                              |
      |                                   | This parameter is not supported for Prometheus instances for cloud services. |
      +-----------------------------------+------------------------------------------------------------------------------+

Discarding Prometheus Instance Metrics
--------------------------------------

If Prometheus instance metrics do not need to be reported, discard them.

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, choose **Prometheus Monitoring** > **Instances**.
#. In the instance list, click a desired Prometheus instance. The instance details page is displayed.
#. In the navigation pane, choose **Metric Management**.
#. Perform the following operations to discard metrics:

   -  To discard a metric, locate it and click |image1| in the **Operation** column.
   -  To discard one or more metrics, select them and click **Delete** in the displayed dialog box.

Adding Prometheus Instance Metrics
----------------------------------

After metrics in a Prometheus instance are discarded, you can add they again.

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, choose **Prometheus Monitoring** > **Instances**.
#. In the instance list, click a desired Prometheus instance. The instance details page is displayed.
#. In the navigation pane, choose **Metric Management**.
#. Click **Add Metric**. In the displayed dialog box, select one or more metrics to restore and click **OK**.

.. |image1| image:: /_static/images/en-us_image_0000002371030065.png
