:original_name: mon_01_0076.html

.. _mon_01_0076:

Configuring the Remote Write Address to Report Self-Built Prometheus Data to AOM
================================================================================

AOM can obtain the remote write address of a Prometheus instance. Native Prometheus metrics can then be reported to AOM through remote write. In this way, time series data can be stored for long.

Prerequisites
-------------

-  You have created an ECS.
-  Your service has been connected for Prometheus monitoring. For details, see :ref:`Managing Prometheus Instances <mon_01_0072>`.

Reporting Self-Built Prometheus Instance Data to AOM
----------------------------------------------------

#. Install and start open-source Prometheus. For details, see `Prometheus official documents <https://prometheus.io/docs/prometheus/latest/getting_started/>`__. (Skip this step if open-source Prometheus has been deployed.)

#. Add an access code.

   a. Log in to the AOM 2.0 console.

   b. In the navigation pane, choose **Settings** > **Global Settings**. The **Global Settings** page is displayed.

   c. On the displayed page, choose **Authentication** in the navigation pane. Click **Add Access Code**.

   d. In the dialog box that is displayed, click **OK**. The system then automatically generates an access code.

      **An access code is an identity credential for calling APIs. A maximum of two access codes can be created for each project. Keep them secure.**

#. .. _mon_01_0076__li5262102016617:

   Obtain the configuration code for Prometheus remote write.

   a. Log in to the AOM 2.0 console.

   b. In the navigation pane on the left, choose **Prometheus Monitoring** > **Instances**. In the instance list, click the name of the target Prometheus instance.

   c. On the displayed page, choose **Settings** in the navigation pane and click |image1| on the right to copy the configuration code for Prometheus remote write from the **Service Addresses** area.


      .. figure:: /_static/images/en-us_image_0000002370949149.png
         :alt: **Figure 1** Configuration code for Prometheus remote write

         **Figure 1** Configuration code for Prometheus remote write

#. Log in to the target ECS and configure the **prometheus.yml** file.

   a. Run the following command to find and start the **prometheus.yml** file:

      .. code-block::

         ./prometheus --config.file=prometheus.yml

   b. Add the configuration code for Prometheus remote write obtained in :ref:`3 <mon_01_0076__li5262102016617>` to the end of the **prometheus.yml** file.

   The following shows an example. You need to configure the italic part.

   .. code-block::

      # my global config
      global:
      scrape_interval:     15s # Set the scrape interval to every 15 seconds. Default is every 1 minute.
      evaluation_interval: 15s # Evaluate rules every 15 seconds. The default is every 1 minute.
      # scrape_timeout is set to the global default (10s).

      # Alertmanager configuration
      alerting:
      alertmanagers:
        - static_configs:
        - targets:
      # - alertmanager:9093

      # Load rules once and periodically evaluate them according to the global 'evaluation_interval'.
      rule_files:
      # - "first_rules.yml"
      # - "second_rules.yml"

      # A scrape configuration containing exactly one endpoint to scrape:
      # Here it's Prometheus itself.
      scrape_configs:
      # The job name is added as a label `job=<job_name>` to any timeseries scraped from this config.
        - job_name: 'prometheus'

      # metrics_path defaults to '/metrics'
      # scheme defaults to 'http'.

      static_configs:
        - targets: ['localhost:9090']
      # Replace the italic content with the configuration code for Prometheus remote write obtained in 3 <mon_01_0076__li5262102016617>.
      remote_write:
        - url:'https://aom-**.***.{Site domain name suffix}:8443/v1/6d6df***2ab7/58d6***c3d/push'
          tls_config:
            insecure_skip_verify: true
          bearer_token: 'SE**iH'

#. Check the private domain name.

   In the preceding example, data is reported through the intranet. Therefore, ensure that the host where Prometheus is located can resolve the private domain name.

#. Restart Prometheus.

#. :ref:`View metric data in AOM using Grafana <mon_01_0077>` to check whether data is successfully reported after the preceding configurations are modified.

.. |image1| image:: /_static/images/en-us_image_0000002336871192.png
