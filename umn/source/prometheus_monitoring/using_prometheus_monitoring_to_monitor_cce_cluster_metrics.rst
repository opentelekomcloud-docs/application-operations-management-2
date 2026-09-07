:original_name: mon_01_0073.html

.. _mon_01_0073:

Using Prometheus Monitoring to Monitor CCE Cluster Metrics
==========================================================

Based on the Prometheus monitoring ecosystem, AOM provides hosted Prometheus instances for CCE, which are suitable for monitoring CCE clusters and applications running on them. By default, Prometheus instances for CCE support integration with the Cloud Native Cluster Monitoring add-on. After installing the add-on, metrics will be automatically reported to a specified Prometheus instance for CCE.

Constraints
-----------

-  Only when the Cloud Native Cluster Monitoring add-on (kube-prometheus-stack) exists on the **Add-ons** page of CCE, can you install the add-on for clusters.
-  Before installing the kube-prometheus-stack add-on, ensure that there are at least 4 vCPUs and 8 GiB memory. Otherwise, this add-on cannot work.

Creating a Prometheus Instance for CCE
--------------------------------------

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, choose **Prometheus Monitoring** > **Instances**. On the displayed page, click **Add Prometheus Instance**.
#. Set an instance name, enterprise project, and instance type.

   .. table:: **Table 1** Parameters for creating a Prometheus instance

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                 |
      +===================================+=============================================================================================================================================================+
      | Instance Name                     | Prometheus instance name.                                                                                                                                   |
      |                                   |                                                                                                                                                             |
      |                                   | Enter a maximum of 100 characters and do not start or end with an underscore (_) or hyphen (-). Only letters, digits, underscores, and hyphens are allowed. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Enterprise Project                | Enterprise project.                                                                                                                                         |
      |                                   |                                                                                                                                                             |
      |                                   | -  If you have selected **All** for **Enterprise Project** on the global settings page, select one from the drop-down list here.                            |
      |                                   | -  If you have already selected an enterprise project on the global settings page, this option will be dimmed and cannot be changed.                        |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Instance Type                     | Type of the Prometheus instance. Select **Prometheus for CCE**.                                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK**.

.. _mon_01_0073__section799564613415:

Connecting a CCE Cluster
------------------------

#. Log in to the AOM 2.0 console.

#. Choose **Prometheus Monitoring** > **Instances**.

#. In the instance list, click a Prometheus instance for CCE.

#. On the **Integration Center** page, click **Connect Cluster**. In the cluster list, you can view the cluster information, installation status, and collection status.

#. Locate a target cluster and click **Install** in the **Operation** column to install the Cloud Native Cluster Monitoring add-on.

#. After the installation is complete, click **Close** to connect the CCE cluster and bind it with the current Prometheus instance.

   To disconnect the CCE cluster, click **Uninstall**.
