:original_name: uiagent_01_0013.html

.. _uiagent_01_0013:

Managing UniAgents and ICAgents in CCE Clusters
===============================================

Kubernetes cluster management allows you to manage the lifecycle of UniAgents and ICAgents on hosts in CCE clusters under your account, for example, batch installation, upgrade, and uninstall.

Prerequisites
-------------

-  You have CCE clusters and nodes under your account.

Viewing the CCE Clusters Connected to AOM
-----------------------------------------

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, choose **Settings** > **Global Settings**.
#. In the navigation pane, choose **Collection Settings** > **K8s Clusters**.
#. On the **K8s Clusters** page, check the CCE clusters connected to AOM.

   -  Enter a CCE cluster name or ID in the search box to search for a cluster. Fuzzy match is supported.
   -  To collect container logs and output them to AOM 1.0, enable **Output to AOM 1.0**. (This function is supported only by ICAgent 5.12.133 or later.) You are advised to collect container logs and output them to LTS instead of AOM 1.0. For details, see `Ingesting CCE Application Logs to LTS <https://docs.otc.t-systems.com/usermanual/lts/lts_04_0511.html>`__.

Managing the UniAgents of CCE Clusters
--------------------------------------

You can install, upgrade, and uninstall UniAgents on hosts in CCE clusters connected to AOM.

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, choose **Settings** > **Global Settings**.
#. On the **Global Settings** page, choose **Collection Settings** > **K8s Clusters** in the navigation pane.
#. On the displayed page, select the target cluster from the cluster list and perform the operations listed in the following table if needed.

   .. table:: **Table 1** Operations on UniAgents

      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                         | Description                                                                                                                                                                                |
      +===================================+============================================================================================================================================================================================+
      | Install UniAgent                  | a. Click **Install UniAgent** and select a UniAgent version to install.                                                                                                                    |
      |                                   | b. Click **OK**. The UniAgent of the specified version and the ICAgent of the latest version will be installed on all hosts of the cluster.                                                |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Upgrade UniAgent                  | a. Click **Upgrade UniAgent** and select a UniAgent version to upgrade.                                                                                                                    |
      |                                   | b. Click **OK**. The UniAgents on all hosts of the cluster will be upgraded to the version you specified.                                                                                  |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Uninstall UniAgent                | a. Click **Uninstall UniAgent**. On the displayed page, click **OK**. The UniAgents will be uninstalled from all hosts of the cluster. ICAgents will also be uninstalled if there are any. |
      |                                   |                                                                                                                                                                                            |
      |                                   |    **Only the UniAgents installed on the K8s Clusters page can be uninstalled here.**                                                                                                      |
      +-----------------------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Managing ICAgents in CCE Clusters
---------------------------------

You can install, upgrade, and uninstall ICAgents on hosts in CCE clusters connected to AOM.

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Settings** > **Global Settings**.

#. On the **Global Settings** page, choose **Collection Settings** > **K8s Clusters** in the navigation pane.

#. On the **K8s Clusters** page, select the cluster where you want to perform ICAgent operations and click **Plug-in Operations**.

   **Plug-in operations are supported only when your UniAgent has been installed through the K8s Clusters page. If your UniAgent is not installed through the K8s Clusters page, click Install UniAgent to install the UniAgent on the hosts in your CCE cluster before performing plug-in operations.**

#. In the displayed dialog box, select the operations listed in the following table if needed.

   .. table:: **Table 2** Plug-in operations

      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Operation                         | Description                                                                                                |
      +===================================+============================================================================================================+
      | Install                           | a. Select the **Install** operation and **ICAgent** plug-in. (Only the ICAgent can be installed.)          |
      |                                   | b. Click **OK**. The ICAgent of the latest version will then be installed on all hosts that meet criteria. |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Upgrade                           | a. Select the **Upgrade** operation and **ICAgent** plug-in. (Only the ICAgent can be upgraded.)           |
      |                                   | b. Click **OK**. The ICAgent on all hosts that meet criteria will then be upgraded to the latest version.  |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
      | Uninstall                         | a. Select the **Uninstall** operation and **ICAgent** plug-in. (Only the ICAgent can be uninstalled.)      |
      |                                   | b. Click **OK**. The ICAgent will then be uninstalled from all hosts that meet criteria.                   |
      +-----------------------------------+------------------------------------------------------------------------------------------------------------+
