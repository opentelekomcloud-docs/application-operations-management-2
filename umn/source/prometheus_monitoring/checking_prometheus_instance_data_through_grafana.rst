:original_name: mon_01_0077.html

.. _mon_01_0077:

Checking Prometheus Instance Data Through Grafana
=================================================

After connecting a cloud service or CCE cluster to a Prometheus instance, you can use Grafana to view the metrics of the cloud service or cluster.

Prerequisites
-------------

-  You have created an ECS.
-  You have created an EIP and bound it to the created ECS.
-  Your service has been connected for Prometheus monitoring. For details, see :ref:`Managing Prometheus Instances <mon_01_0072>`.

Procedure
---------

#. Install and start Grafana. For details, see the `Grafana official documentation <https://grafana.com/docs/grafana/latest/installation/>`__.
#. Add an access code.

   a. Log in to the AOM 2.0 console.

   b. In the navigation pane, choose **Settings** > **Global Settings**. The **Global Settings** page is displayed.

   c. On the displayed page, choose **Authentication** in the navigation pane. Click **Add Access Code**.

   d. In the dialog box that is displayed, click **OK**. The system then automatically generates an access code.

      **An access code is an identity credential for calling APIs. A maximum of two access codes can be created for each project. Keep them secure.**

#. Obtain the Grafana data source configuration code.

   a. Log in to the AOM 2.0 console.

   b. In the navigation pane on the left, choose **Prometheus Monitoring** > **Instances**. In the instance list, click the name of the target Prometheus instance.

   c. .. _mon_01_0077__li45971550185511:

      On the displayed page, choose **Settings** in the navigation pane and obtain the Grafana data source information from the **Grafana Data Source Info** area.

#. Configure Grafana.

   a. Log in to Grafana.

   b. In the navigation pane, choose **Connections** > **Data Sources**. Then click **Add data source**.

      (Configuration parameters may vary depending on the Grafana version. Configure the parameters based on site requirements.)

   c. Click **Prometheus** to access the configuration page.


      .. figure:: /_static/images/en-us_image_0000002336872468.png
         :alt: **Figure 1** Prometheus configuration page

         **Figure 1** Prometheus configuration page

   d. Set Grafana data source parameters.

      -  **Prometheus server URL**: HTTP URL obtained in :ref:`3.c <mon_01_0077__li45971550185511>`.
      -  **User**: username obtained in :ref:`3.c <mon_01_0077__li45971550185511>`.
      -  **Password**: password obtained in :ref:`3.c <mon_01_0077__li45971550185511>`.

      The **Basic auth** and **Skip TLS Verify** options under **Auth** must be enabled.


      .. figure:: /_static/images/en-us_image_0000002370950409.png
         :alt: **Figure 2** Setting parameters

         **Figure 2** Setting parameters

      If the current version supports the configuration of performance parameters under **Advanced settings**, set **Prometheus type** to **Cortex** and **Cortex version** to **1.0.0**.

      |image1|

   e. Click **Save&Test** to check whether the configuration is successful.

      If the configuration is successful, you can use Grafana to `configure dashboards <https://grafana.com/docs/grafana/latest/dashboards/build-dashboards/create-dashboard/>`__ and view metric data.


      .. figure:: /_static/images/en-us_image_0000002371030565.png
         :alt: **Figure 3** Checking whether the configuration is successful

         **Figure 3** Checking whether the configuration is successful

.. |image1| image:: /_static/images/en-us_image_0000002370950405.png
