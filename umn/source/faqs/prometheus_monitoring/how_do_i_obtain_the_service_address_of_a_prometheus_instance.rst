:original_name: aom_06_0064.html

.. _aom_06_0064:

How Do I Obtain the Service Address of a Prometheus Instance?
=============================================================

You can log in to the AOM console and go to the Prometheus instance details page to obtain the service address of the Prometheus instance.

Procedure:

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Prometheus Monitoring** > **Instances**. In the instance list, click the target Prometheus instance.

#. On the instance details page, choose **Settings** in the navigation pane to obtain the service address of the current instance.

   The following describes how to obtain the service address of a Prometheus instance for CCE.

   -  Click the **Intranet** tab to obtain the configuration code for Prometheus remote read and write in the intranet. Click |image1| on the right of the code to copy the code to the corresponding file.

   -  Obtain the configuration code for Prometheus remote read.


      .. figure:: /_static/images/en-us_image_0000002337031512.png
         :alt: **Figure 1** Configuration code for Prometheus remote read

         **Figure 1** Configuration code for Prometheus remote read

      Remote read address:

      .. code-block::

         url: 'https://aom.{region_name}.{Site domain name suffix}/v1/{project_id}/api/v1/read'

      Remote read address parameters:

      -  **region_name**: domain name or IP address of the server where the REST service is deployed. The value varies depending on services and regions.
      -  **Site domain name suffix**: site domain name suffix.
      -  **project_id**: project ID.

   -  Obtain the configuration code for Prometheus remote write.


      .. figure:: /_static/images/en-us_image_0000002371029885.png
         :alt: **Figure 2** Configuration code for Prometheus remote write

         **Figure 2** Configuration code for Prometheus remote write

      Remote write address in the intranet:

      .. code-block::

         url: 'https://aom-internal-access.{region_name}.{Site domain name suffix}:8443/v1/{project_id}/push'

      Remote write address parameters:

      -  **region_name**: domain name or IP address of the server where the REST service is deployed. The value varies depending on services and regions.
      -  **Site domain name suffix**: site domain name suffix.
      -  **project_id**: project ID.

.. |image1| image:: /_static/images/en-us_image_0000002371029881.png
