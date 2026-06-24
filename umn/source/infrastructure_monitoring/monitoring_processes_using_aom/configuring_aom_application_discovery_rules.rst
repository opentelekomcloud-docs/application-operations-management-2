:original_name: mon_01_0087.html

.. _mon_01_0087:

Configuring AOM Application Discovery Rules
===========================================

AOM can discover applications and components and collect their metrics based on configured rules. There are two modes to configure application discovery: auto mode and manual mode. This section mainly describes the manual mode.

-  **Auto mode**

   After you install the ICAgent on a host, the ICAgent automatically discovers applications or components on the host based on :ref:`Built-in Discovery Rules <mon_01_0087__section938317591962>` and displays them on the application or component monitoring page.

-  **Manual mode**

   If you customize an application discovery rule and apply it to the host where the ICAgent is installed, the ICAgent discovers applications on the host based on the custom rule and displays them on the **Application Monitoring** page.

Filtering Rule Description
--------------------------

The ICAgent periodically detects processes on the target host. The effect is similar to that of running the **ps -e -o pid,comm,lstart,cmd \| grep -v defunct** command. Then, the ICAgent checks whether processes match the filtering rules in :ref:`Table 1 <mon_01_0087__table11580171542711>`. If a process meets a filtering rule, the process is filtered out and is not discovered by AOM. If a process does not meet any filtering rules, the process is not filtered and is discovered by AOM.

Information similar to the following is displayed:

.. code-block::

      PID COMMAND                          STARTED CMD
        1 systemd         Tue Oct  2 21:12:06 2018 /usr/lib/systemd/systemd --switched-root --system --deserialize 20
        2 kthreadd        Tue Oct  2 21:12:06 2018 [kthreadd]
        3 ksoftirqd/0     Tue Oct  2 21:12:06 2018 (ksoftirqd/0)
     1140 tuned           Tue Oct  2 21:12:27 2018 /usr/bin/python -Es /usr/sbin/tuned -l -P
     1144 sshd            Tue Oct  2 21:12:27 2018 /usr/sbin/sshd -D
     1148 agetty          Tue Oct  2 21:12:27 2018 /sbin/agetty --keep-baud 115200 38400 9600 hvc0 vt220
     1154 docker-containe Tue Oct  2 21:12:29 2018 docker-containerd -l unix:///var/run/docker/libcontainerd/docker-containerd.sock --shim docker-containerd-shim --start-timeout 2m --state-dir /var/run/docker/libcontainerd/containerd --runtime docker-runc --metrics-interval=0

.. _mon_01_0087__table11580171542711:

.. table:: **Table 1** Filtering rules

   +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | Filtering Rule                                                                                                                                                                                                                                                                       | Example                                                                                                                                            |
   +======================================================================================================================================================================================================================================================================================+====================================================================================================================================================+
   | If the **COMMAND** value of a process is **docker-containe**, **vi**, **vim**, **pause**, **sshd**, **ps**, **sleep**, **grep**, **tailf**, **tail**, or **systemd-udevd**, and the process is not running in a container, the process is filtered out and is not discovered by AOM. | In the preceding information, the process whose **PID** is **1154** is not discovered by AOM because its **COMMAND** value is **docker-containe**. |
   +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | If the **CMD** value of a process starts with **[** and ends with **]**, the process is filtered out and is not discovered by AOM.                                                                                                                                                   | In the preceding information, the process whose **PID** is **2** is not discovered by AOM because its **CMD** value is **[kthreadd]**.             |
   +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | If the **CMD** value of a process starts with **(** and ends with **)**, the process is filtered out and is not discovered by AOM.                                                                                                                                                   | In the preceding information, the process whose **PID** is **3** is not discovered by AOM because its **CMD** value is **(ksoftirqd/0)**.          |
   +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
   | If the **CMD** value of a process starts with **/sbin/**, the process is filtered out and is not discovered by AOM.                                                                                                                                                                  | In the preceding information, the process whose **PID** is **1148** is not discovered by AOM because its **CMD** value starts with **/sbin/**.     |
   +--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. _mon_01_0087__section938317591962:

Built-in Discovery Rules
------------------------

AOM provides two built-in discovery rules: **Sys_Rule** and **Default_Rule**. These rules are executed on all hosts, including hosts added later. The priority of **Sys_Rule** is higher than that of **Default_Rule**. That is, **Sys_Rule** is executed on the host first. If **Sys_Rule** is met, **Default_Rule** is not executed. Otherwise, **Default_Rule** is executed. Rule details are as follows:

**Sys_Rule** (cannot be disabled)

When **Sys_Rule** is used, the component name and application name must be used together. The names are determined according to the following priorities:

-  Priorities for determining the application name:

   #. .. _mon_01_0087__li13359524711:

      Use the value of the **Dapm_application** field in the process startup command.

   #. .. _mon_01_0087__li163611758172:

      If the value in :ref:`1 <mon_01_0087__li13359524711>` is empty, use the value of the **Dapm_application** field in the **JAVA_TOOL_OPTIONS** variable.

   #. .. _mon_01_0087__li2431432818:

      If the value in :ref:`2 <mon_01_0087__li163611758172>` is empty, use the value of the **PAAS_MONITORING_GROUP** variable.

   #. If the value in :ref:`3 <mon_01_0087__li2431432818>` is empty, use the value of the **DAOM.APPN** field in the process startup command.

-  Priorities for determining the component name:

   #. .. _mon_01_0087__li65881258193:

      Use the value of the **DAOM.PROCN** field in the process startup command. If the value is empty, use the value of the **Dapm_tier** field.

   #. .. _mon_01_0087__li2435142311119:

      If the value in :ref:`1 <mon_01_0087__li65881258193>` is empty, use the value of the **Dapm_tier** field in the **JAVA_TOOL_OPTIONS** variable.

   #. If the value in :ref:`2 <mon_01_0087__li2435142311119>` is empty, use the value of the **PAAS_APP_NAME** variable.

In the following example, the component name is **atps-demo** and the application name is **atpd-test**.

.. code-block:: text

   PAAS_MONITORING_GROUP=atpd-test
   PAAS_APP_NAME=atps-demo
   JAVA_TOOL_OPTIONS=-javaagent:/opt/oss/servicemgr/ICAgent/pinpoint/pinpoint-bootstrap.jar -Dapm_application=atpd-test -Dapm_tier=atps-demo

**Default_Rule** (can be disabled)

-  If the **COMMAND** value of a process is **java**, obtain the name of the JAR package in the command, the main class name in the command, and the first keyword that does not start with a hyphen (-) in the command based on the priorities in descending order as the component name, and use the default value **unknownapplicationname** as the application name.
-  If the **COMMAND** value of a process is **python**, obtain the name of the first **.py**/**.pyc** script in the command as the component name, and use the default value **unknownapplicationname** as the application name.
-  If the **COMMAND** value of a process is **node**, obtain the name of the first **.js** script in the command as the component name, and use the default value **unknownapplicationname** as the application name.

Customizing a Discovery Rule
----------------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Infrastructure Monitoring** > **Process Monitoring**. Next, click the **Application Discovery** tab.

#. On the displayed page, click **Add Custom Application Discovery Rule** and configure an application discovery rule.

#. Select a host for pre-detection.

   a. Customize a rule name, for example, **rule-test**. Enter 4 to 63 characters starting with a lowercase letter and ending with a lowercase letter or digit. Only lowercase letters, digits, and hyphens (-) are allowed.
   b. Select a typical host, for example, **host-test**, to check whether the application discovery rule is valid. The hosts that execute the rule will be configured in :ref:`7 <mon_01_0087__li1434613512472>`. Then click **Next**.

#. Set an application discovery rule.

   a. Click **Add Check Items**. AOM can discover processes that meet the conditions of check items. Enter 1 to 255 characters.

      For example, AOM can detect the processes whose command parameters contain **ovs-vswitchd unix:** and environment variables contain **SUDO_USER=paas**.

      -  To precisely detect processes, you are advised to add check items about unique features of the processes.
      -  You must add at least one check item and can add up to five check items. If there are multiple check items, AOM only discovers the processes that meet the conditions of all check items.

   b. After adding check items, click **Detect** to search for the processes that meet the conditions.

      If no process is detected within 20s, modify the discovery rule and detect processes again. Only when at least one process is detected can you proceed to the next step.

#. Set an application name and component name.

   a. Set an application name.

      In the **Application Name Settings** area, click **Add Naming Rule** to set an application name for the detected process. Enter 1 to 255 characters.

      -  If you do not set an application name, the default name **unknownapplicationname** is used.
      -  When you add multiple naming rules, all the naming rules are combined as the application name of the process. Metrics of the same application are aggregated.

   b. Set a component name.

      In the **Component Name Settings** area, specify an application type and click **Add Naming Rule** to set a component name for the discovered process. Enter 1 to 255 characters. For example, add the text **app-test** as a component name.

      -  Application types indicate application categories. They are used only for better rule classification and console display. You can enter any field. For example, enter **Java** or **Python** by technology stack, or enter **collector** or **database** by function.
      -  If you do not set a component name, the default name **unknownapplicationname** is used.
      -  When you add multiple naming rules, all the naming rules are combined as the component name of the process. Metrics of the same component are aggregated.

   c. Preview the component name.

      If the name does not meet your requirements, click |image1| in the **Preview Component Name** table to rename the component.

#. .. _mon_01_0087__li1434613512472:

   Set a priority and detection range.

   a. Set a priority: When there are multiple rules, set priorities. Enter 1 to 9999. A smaller value indicates a higher priority. For example, **1** indicates the highest priority and **9999** indicates the lowest priority.
   b. Set a detection range: Select a host to be detected. That is, select the host to which the configured rule is applied. If no host is selected, this rule will be executed on all hosts, including hosts added later.

#. Click **OK** to complete the configuration.

   AOM then collects metric data based on the discovery rule. After about two minutes, you can perform the following operations:

   -  On the **Application Monitoring** tab page, find the monitored application. For details, see :ref:`Using AOM to Monitor Application Processes <mon_01_0085>`.
   -  On the **Component Monitoring** tab page, find the monitored component. For details, see :ref:`Using AOM to Monitor Component Processes <mon_01_0086>`.

More Operations
---------------

After creating an application discovery rule, perform the operations listed in :ref:`Table 2 <mon_01_0087__table62191141172620>` if needed.

.. _mon_01_0087__table62191141172620:

.. table:: **Table 2** Related operations

   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Operation                         | Description                                                                                                                  |
   +===================================+==============================================================================================================================+
   | Viewing rule details              | In the **Name** column, click the name of an application discovery rule.                                                     |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Starting or stopping rules        | -  Click **Start** in the **Operation** column.                                                                              |
   |                                   | -  Click **Stop** in the **Operation** column. After a rule is disabled, AOM does not collect corresponding process metrics. |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Deleting rules                    | -  To delete a discovery rule, click **Delete** in the **Operation** column.                                                 |
   |                                   | -  To delete one or more application discovery rules, select them and click **Delete** above the rule list.                  |
   |                                   |                                                                                                                              |
   |                                   | **Built-in discovery rules cannot be deleted.**                                                                              |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Modifying rules                   | Click **Modify** in the **Operation** column.                                                                                |
   |                                   |                                                                                                                              |
   |                                   | **Built-in discovery rules cannot be modified.**                                                                             |
   +-----------------------------------+------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002337030788.png
