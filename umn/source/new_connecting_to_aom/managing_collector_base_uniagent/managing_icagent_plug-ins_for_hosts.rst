:original_name: uiagent_01_0028.html

.. _uiagent_01_0028:

Managing ICAgent Plug-ins for Hosts
===================================

AOM will support interconnection with other types of plug-ins. You can install, upgrade, uninstall, start, stop, and restart plug-ins in batches for hosts.

Currently, only ICAgents are supported. An ICAgent is a plug-in for collecting metrics and logs. ICAgent collects data at an interval of 1 minute. This interval cannot be changed.

Managing ICAgent Plug-ins in Batches
------------------------------------

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, choose **Settings** > **Global Settings**.
#. In the navigation pane on the left, choose **Collection Settings** > **UniAgents**. The old VM access page is displayed. You can click **Try New Version** in the upper right corner to go to the new UniAgent management page.
#. Select one or more target servers and click **Plug-in Batch Operation**.
#. In the displayed dialog box, select an operation type, set the plug-in information, and click **OK**. (When selecting a CCE host, you are advised to go to the :ref:`K8s Clusters <agent_01_0013>` page to operate the ICAgent.)

   .. table:: **Table 1** Plug-in operation parameters

      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                                             |
      +===================================+=========================================================================================================================================================================================================+
      | Operation                         | The following batch operations are supported: install, upgrade, uninstall, start, stop, and restart.                                                                                                    |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Plug-in                           | Select the plug-in to be operated. The ICAgent of the latest version can be installed.                                                                                                                  |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | AK/SK                             | Access Key ID/Secret Access Key (AK/SK) to be entered based on your plug-in type and version.                                                                                                           |
      |                                   |                                                                                                                                                                                                         |
      |                                   | **You need to enter an AK/SK only when installing the ICAgent of an earlier version. (If there is no text box for you to enter the AK/SK, the ICAgent of the new version has already been installed.)** |
      |                                   |                                                                                                                                                                                                         |
      |                                   | Procedure to obtain an AK/SK:                                                                                                                                                                           |
      |                                   |                                                                                                                                                                                                         |
      |                                   | a. Hover over the username at the upper right corner and select **My Credentials** from the drop-down list.                                                                                             |
      |                                   | b. Choose **Access Keys** in the navigation pane. On the displayed page, click **Create Access Key** above the list, enter the key description, and click **OK**.                                       |
      |                                   | c. Click **Download**. Obtain the AK and SK from the credential file.                                                                                                                                   |
      +-----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
