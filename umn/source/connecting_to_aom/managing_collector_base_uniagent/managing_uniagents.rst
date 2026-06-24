:original_name: agent_01_0006.html

.. _agent_01_0006:

Managing UniAgents
==================

After UniAgents are installed, you can reinstall, upgrade, uninstall, or delete them when necessary.

Constraints
-----------

-  If the host where a UniAgent is installed runs Windows, you need to manually reinstall or uninstall the UniAgent.
-  UniAgents will not be automatically upgraded. Manually upgrade them if needed.
-  During UniAgent management, if CCE cluster-hosted servers are selected or the UniAgent has already been installed on the **K8s Clusters** page, go to the :ref:`K8s Clusters <agent_01_0013>` page to manage the UniAgent.

Reinstalling UniAgents
----------------------

Reinstall UniAgents when they are offline or not installed or fail to be installed.

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, choose **Settings** > **Global Settings**.
#. In the navigation pane on the left, choose **Collection Settings** > **UniAgents**. The old VM access page is displayed. You can click **Try New Version** in the upper right corner to go to the new UniAgent management page.
#. Select one or more servers where UniAgents are to be reinstalled and perform the following operations:

   -  (Old) On the **VM Access** page, choose **UniAgent Batch Operation** > **Reinstall**. On the displayed page, :ref:`reinstall UniAgents <agent_01_0005>` as prompted.
   -  (New) On the **UniAgents** page, switch to the **ECS** or **Other** tab page and click **Reinstall**. On the displayed page, :ref:`reinstall UniAgents <agent_02_0005>` as prompted. (If CCE cluster-hosted servers are selected or the UniAgent has already been installed on the **K8s Clusters** page, go to the :ref:`K8s Clusters <agent_01_0013>` page to reinstall the UniAgent.)

Upgrading UniAgents
-------------------

Upgrade your UniAgent to a more reliable, stable new version.

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Settings** > **Global Settings**.

#. In the navigation pane on the left, choose **Collection Settings** > **UniAgents**. The old VM access page is displayed. You can click **Try New Version** in the upper right corner to go to the new UniAgent management page.

#. Select one or more servers where UniAgents are to be upgraded and perform the following operations:

   -  (Old) On the **VM Access** page, choose **UniAgent Batch Operation** > **Upgrade**. On the displayed page, select the target version and click **OK**.
   -  (New) On the **UniAgents** page, switch to the **ECS** or **Other** tab page and click **Upgrade**. On the displayed page, select the target version and click **OK**. (If CCE cluster-hosted servers are selected or the UniAgent has already been installed on the **K8s Clusters** page, go to the :ref:`K8s Clusters <agent_01_0013>` page to upgrade the UniAgent.)

   Wait for about 1 minute until the UniAgent upgrade is complete.

Uninstalling UniAgents
----------------------

Uninstall UniAgents when necessary.

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Settings** > **Global Settings**.

#. In the navigation pane on the left, choose **Collection Settings** > **UniAgents**. The old VM access page is displayed. You can click **Try New Version** in the upper right corner to go to the new UniAgent management page.

#. Select one or more servers where UniAgents are to be uninstalled and perform the following operations:

   -  (Old) On the **VM Access** page, choose **UniAgent Batch Operation** > **Uninstall**. On the displayed page, click **OK**.
   -  (New) On the **UniAgents** page, switch to the **ECS** or **Other** tab page and click **Uninstall**. On the displayed page, click **OK**. (If CCE cluster-hosted servers are selected or the UniAgent has already been installed on the **K8s Clusters** page, go to the :ref:`K8s Clusters <agent_01_0013>` page to uninstall the UniAgent.)

   You can also log in to the target server as the **root** user and run the following command to uninstall the UniAgent:

   **bash /usr/local/uniagentd/bin/uninstall_uniagent.sh;**

Deleting UniAgents
------------------

Delete the UniAgents that are not used or cannot be used according to the following procedure:

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, choose **Settings** > **Global Settings**.
#. In the navigation pane on the left, choose **Collection Settings** > **UniAgents**. The old VM access page is displayed. You can click **Try New Version** in the upper right corner to go to the new UniAgent management page.
#. Select one or more servers where UniAgents are to be deleted and perform the following operations:

   -  (Old) On the **VM Access** page, choose **UniAgent Batch Operation** > **Delete**. On the displayed page, click **OK**.
   -  (New) On the **UniAgents** page, switch to the **ECS** or **Other** tab page and click **Delete**. On the displayed page, click **OK**.
