:original_name: mon_01_0054.html

.. _mon_01_0054:

Migrating Data from AOM 1.0 to AOM 2.0
======================================

This section describes how to migrate data from AOM 1.0 to AOM 2.0. Currently, only collector and alarm rule upgrades are supported.

Function Introduction
---------------------

-  :ref:`Collector Upgrade <mon_01_0054__section1967411301414>`

   After the collector is upgraded, the process discovery capability is enhanced and the collector can automatically adapt to functions related to CMDB, and monitoring center.

-  :ref:`Alarm Rule Upgrade <mon_01_0054__section19675181391416>`

   After alarm rules are upgraded, alarm rule data is smoothly switched from AOM 1.0 to AOM 2.0, and is automatically adapted to alarm rule functions of AOM 2.0.

.. _mon_01_0054__section1967411301414:

Collector Upgrade
-----------------

#. Log in to the AOM 1.0 console.

#. In the navigation pane, choose **Configuration Management** > **Agent Management**.

#. Select **Other: custom hosts** from the drop-down list on the right of the page.

#. Select a host and click **Upgrade ICAgent**.

#. Select a target AOM 2.0 version from the drop-down list and click **OK**.

#. Wait for the upgrade. This process takes about a minute. When the ICAgent status changes from **Upgrading** to **Running**, the upgrade is successful.

   If the ICAgent is abnormal after the upgrade or if the upgrade fails, log in to the host and run the installation command again. Note that there is no need for you to uninstall the original ICAgent.

.. _mon_01_0054__section19675181391416:

Alarm Rule Upgrade
------------------

#. Log in to the AOM 1.0 console.

#. In the navigation pane on the left, choose **Alarm Center** > **Alarm Rules**.

#. Select one or more alarm rules and click **Migrate to AOM 2.0** above the rule list.

   Precautions:

   -  Migration cannot be undone.
   -  If the alarm rules to be migrated depend on alarm templates, these alarm templates will also be migrated.

4. In the displayed dialog box, click **Confirm**. The selected alarm rules will be migrated to AOM 2.0 in batches.
