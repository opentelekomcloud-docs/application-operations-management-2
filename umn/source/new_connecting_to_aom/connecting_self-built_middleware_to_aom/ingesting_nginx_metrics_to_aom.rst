:original_name: mon_01_0216.html

.. _mon_01_0216:

Ingesting Nginx Metrics to AOM
==============================

Install the Nginx Exporter provided by AOM, and then create a collection task by setting a metric ingestion rule to monitor Nginx metrics on a host.

Prerequisites
-------------

-  :ref:`The UniAgent has been installed <uiagent_02_0005>` and is running.
-  :ref:`A Prometheus instance for ECS or a common Prometheus instance <mon_01_0072>` has been created.

-  :ref:`The NGINX stub_status module has been enabled <mon_01_0216__section414913234597>`.
-  To use the new Nginx Exporter ingestion function, switch to the new access center.

.. _mon_01_0216__section414913234597:

Enabling the Nginx stub_status Module
-------------------------------------

Nginx Prometheus Exporter monitors the Nginx service using the stub_status module. Ensure that this module is enabled.

#. Log in to the node where the Nginx service is deployed and run the following command (generally in the **/usr/local/nginx/sbin/nginx** directory) as the **root** user to check whether the stub_status module is enabled:

   .. code-block::

      nginx -V 2>&1 | grep -o with-http_stub_status_module

   -  If **with-http_stub_status_module** is returned, the stub_status module is enabled.

   -  If no result is returned, enable the stub_status module by setting **--with-http_stub_status_module** in the configuration file. Example:

      .. code-block::

         ./configure \
         ## Add the --with-http_stub_status_module parameter.
         --with-http_stub_status_module
         make
         sudo make install

#. After the stub_status module is enabled, add the following content to the **nginx.conf** file (which is generally in the **/usr/local/nginx/conf** directory): Example:

   a. Open the **nginx.conf** file using the vi editor:

      .. code-block::

         vi /usr/local/nginx/conf/nginx.conf

   b. Press **i** to enter the editing mode and add the following configuration information:

      .. code-block::

         server {
          listen 8080;  # Listening port. Set this parameter based on service requirements.
          listen [::]:8080; # IPv6 listening port. Set this parameter based on service requirements.
          server_name localhost; # Set this parameter based on service requirements.
          location = /stub_status { # Path. Set this parameter based on service requirements.
              stub_status on;
              access_log off;
              allow 127.0.0.1;
          }
         }

   c. Press **Esc** and enter **:wq** to save the settings and exit.

#. Restart the Nginx service.

Connecting Nginx Exporter to AOM
--------------------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Access Center** > **Access Center**, filter the **NGINX** card under **Self-built middleware**, and click **Ingest Metric (AOM)**.

#. On the displayed page, set parameters.

   a. Set the Prometheus instance.

      #. **Instance Type**: Select a Prometheus instance type. Options: **Prometheus for ECS** and **Common Prometheus instance**.

      #. **Instance Name**: Select a Prometheus instance from the drop-down list and click **Next**.

         You can click **View Instance** to go to the details page of the selected instance. If no Prometheus instance is available, click **Create Instance** to :ref:`create a Prometheus instance for ECS or a common Prometheus instance <mon_01_0072>`.

   b. Install the plug-in and test the connectivity.

      #. Set parameters to install the plug-in by referring to the following table.

         .. table:: **Table 1** Parameters

            +----------------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Operation                        | Parameter             | Description                                                                                                                                                                                                                                                 |
            +==================================+=======================+=============================================================================================================================================================================================================================================================+
            | Basic Settings                   | Ingestion Rule Name   | Name of a custom metric ingestion rule. Enter 1 to 50 characters starting with a letter. Only letters, digits, underscores (_), and hyphens (-) are allowed.                                                                                                |
            +----------------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Set Collection Plug-in           | OS                    | Operating system of the host. Only Linux is supported.                                                                                                                                                                                                      |
            +----------------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            |                                  | Collection Plug-in    | The default value is **Nginx Exporter**. Select a plug-in version.                                                                                                                                                                                          |
            +----------------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Select Server to Install Plug-in | Select Server         | Click **Select Server** to select a running server to configure a collection task and install Exporter.                                                                                                                                                     |
            |                                  |                       |                                                                                                                                                                                                                                                             |
            |                                  |                       | -  On the **Select Server** page, search for servers by server ID, name, status, or IP address.                                                                                                                                                             |
            |                                  |                       | -  Ensure that the UniAgent of the selected server is running. Otherwise, no data can be collected.                                                                                                                                                         |
            |                                  |                       | -  If no server meets your requirements, UniAgent may be not installed. In that case, :ref:`install UniAgent <uiagent_02_0005>`. In addition, ensure that the UniAgent version is 1.1.3 or later. :ref:`Upgrade UniAgent <uiagent_01_0006>` when necessary. |
            +----------------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
            | Connect Nginx Instance           | Nginx URL             | Nginx URL, which is in the format of "Connection address of Nginx+Nginx service status path".                                                                                                                                                               |
            |                                  |                       |                                                                                                                                                                                                                                                             |
            |                                  |                       | -  Connection address of Nginx: IP address and listening port number of the Nginx service. The listening port is specified in the **nginx.conf** file. Example: **10.0.0.1:8080**                                                                           |
            |                                  |                       | -  Nginx service status path: specified by the **location** parameter in the **nginx.conf** file, for example, **/stub_status**.                                                                                                                            |
            |                                  |                       |                                                                                                                                                                                                                                                             |
            |                                  |                       | Example: **https://10.0.0.1:8080/stub_status**.                                                                                                                                                                                                             |
            +----------------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

      #. Click **Install & Test Collection Plug-in** to deliver the Exporter installation task.

         -  After the plug-in is installed, click **Next**.
         -  Click **View Log** to view Exporter installation logs if the installation fails.

   c. Set an ingestion rule.

      Set a metric ingestion rule by referring to the following table.

      .. table:: **Table 2** Parameters

         +------------------------+--------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Operation              | Parameter                      | Description                                                                                                                                                                            |
         +========================+================================+========================================================================================================================================================================================+
         | Metric Collection Rule | Metric Collection Interval (s) | Interval for collecting metrics, in seconds. Options: **10**, **30**, and **60** (default).                                                                                            |
         +------------------------+--------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                        | Metric Collection Timeout (s)  | Timeout period for executing a metric collection task, in seconds. Options: **10**, **30**, and **60** (default).                                                                      |
         |                        |                                |                                                                                                                                                                                        |
         |                        |                                | The timeout period cannot exceed the collection interval.                                                                                                                              |
         +------------------------+--------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         |                        | Executor                       | User who executes the metric ingestion rule, that is, the user of the selected server. By default, the executor is **root**.                                                           |
         +------------------------+--------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Other                  | Custom Dimensions              | Dimensions (key-value pairs) added to specify additional metric attributes. You can click **Add Dimension** to add multiple custom dimensions (key-value pairs).                       |
         |                        |                                |                                                                                                                                                                                        |
         |                        |                                | -  Key: key of the additional attribute of a metric. Only letters, digits, and underscores (_) are allowed. Each name must start with a letter or underscore. Each key must be unique. |
         |                        |                                | -  Value: corresponds to the key of the additional attribute of a metric. The following characters are not allowed: ``&|><$;'!-()``                                                    |
         |                        |                                |                                                                                                                                                                                        |
         |                        |                                | Up to 10 dimensions can be added. Example: Set the key to **app** and value to **abc**.                                                                                                |
         +------------------------+--------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

      After the metric collection rule parameters are configured, you can click **YAML** to view the configuration data in YAML format.

#. Click **Next** to connect Nginx Exporter.

   After Nginx Exporter is connected, perform the following operations if needed:

   -  Back to the access center to connect other data sources. For details, see :ref:`AOM Access Overview <mon_01_0196>`.
   -  Go to the **Access Management** page to view and manage the ingestion configuration of the Exporter. For details, see :ref:`Managing Metric and Log Ingestion <mon_01_0206>`.
   -  Go to the **Metric Browsing** page to analyze metrics. For details, see :ref:`Observability Metric Browsing <mon_01_0026>`.
