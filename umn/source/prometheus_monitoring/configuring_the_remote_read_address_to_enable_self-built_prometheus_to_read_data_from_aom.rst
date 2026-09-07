:original_name: mon_01_0124.html

.. _mon_01_0124:

Configuring the Remote Read Address to Enable Self-built Prometheus to Read Data from AOM
=========================================================================================

Prometheus monitoring provides the remote read API, which can categorize a series of Prometheus protocol data sources into a single data source for query. This section describes how to read AOM Prometheus instance data through the remote read API when you use self-built Prometheus.

Constraints
-----------

When configuring Prometheus for remote read, ensure that **global:external_labels**:** is correct since **external_labels** will be added to the search criteria. If a label is incorrect, required data may fail to be queried.

You can set **filter_external_labels: false** (Prometheus: v2.34 or later) to prevent **external_labels** from being added to the search criteria.

Prerequisite
------------

Your service has been connected for Prometheus monitoring. For details, see :ref:`Managing Prometheus Instances <mon_01_0072>`.

Configuring the Remote Read Address
-----------------------------------

You are advised to configure the **prometheus.yml** file of self-built Prometheus. Procedure:

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Prometheus Monitoring** > **Instances**. In the instance list, click the target Prometheus instance to go to the details page.

#. In the navigation pane on the left, choose **Settings**. On the **Intranet** tab page in the **Service Addresses** area, click |image1| on the right to copy the configuration code for Prometheus remote read.

   .. code-block::

      remote_read:
        - url: 'https://aom.{region_name}.{Site domain name suffix}/v1/{project_id}/{prometheus_instance_id}/api/v1/read'
          tls_config:
            insecure_skip_verify: true
           bearer_token: '8H**LP'
           read_recent: true

#. Add the copied configuration code to the **prometheus.yml** file of self-built Prometheus.

#. Restart the self-built Prometheus service.

   Then you can view AOM Prometheus data.

Complete Configuration Items of Remote Read
-------------------------------------------

The configuration items in brackets ([]) are optional. The following lists the configurations of Prometheus v2.40. Some configuration items may be unavailable in earlier versions. For details, see `Prometheus official documents <https://prometheus.io/docs/prometheus/latest/configuration/configuration/#remote_read>`__.

.. code-block::

   # API URL of the target Prometheus instance for remote read
   url: <string>

   # Unique name of a configuration for remote read
   [ name: <string> ]

   # Filtering conditions that must be contained in PromQL for remote read
   required_matchers:
     [ <labelname>: <labelvalue> ... ]

   # Timeout for remote read query
   [ remote_timeout: <duration> | default = 1m ]

   # Custom headers attached to remote read requests, which cannot overwrite the headers added by Prometheus
   headers:
     [ <string>: <string> ... ]

   # Whether to directly read metrics from the local storage during Prometheus remote read
   [ read_recent: <boolean> | default = false ]

   # Add an authorization header for each remote read request. Select either password or password_file.
   basic_auth:
     [ username: <string> ]
     [ password: <secret> ]
     [ password_file: <string> ]

   # Custom authorization header configuration
   authorization:
     # Authentication type
     [ type: <string> | default: Bearer ]
     #Authentication key. Select either credentials or credentials_file.
     [ credentials: <secret> ]
   # Obtain the key from a file.
     [ credentials_file: <filename> ]

   # OAuth 2.0 authentication, which cannot be used together with basic_auth authorization
   oauth2:
     [ <oauth2> ]

   # TLS configuration
   tls_config:
     [ <tls_config> ]

   # Proxy URL
   [ proxy_url: <string> ]

   # Whether 3XX redirection is allowed
   [ follow_redirects: <boolean> | default = true ]

   # Whether to enable HTTP2
   [ enable_http2: <bool> | default: true ]

   # Whether to attach external_labels during remote read
   [ filter_external_labels: <boolean> | default = true ]

.. |image1| image:: /_static/images/en-us_image_0000002336872076.png
