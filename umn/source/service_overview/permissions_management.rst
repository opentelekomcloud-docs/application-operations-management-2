:original_name: aom_01_0019.html

.. _aom_01_0019:

Permissions Management
======================

If you need to assign different permissions to employees in your enterprise to access your AOM resources, Identity and Access Management (IAM) is a good choice for fine-grained permissions management. IAM provides identity authentication, permissions management, and access control, helping you secure access to your AOM resources.

With IAM, you can use your account to create IAM users for your employees, and assign permissions to the users to control their access to specific types of resources. For example, some software developers in your enterprise need to use AOM resources but are not allowed to delete them or perform any high-risk operations such as deleting application discovery rules. To achieve this result, you can create IAM users for the software developers and grant them only the permissions required for using AOM resources.

If your account does not need individual IAM users for permissions management, you may skip over this chapter.

IAM can be used free of charge. You pay only for the resources in your account. For more information, see `IAM Service Overview <https://docs.otc.t-systems.com/usermanual/iam/iam_01_0026.html>`__.

AOM Permissions
---------------

By default, new IAM users do not have any permissions assigned. You need to add a user to one or more groups, and assign permissions policies or roles to these groups. The user then inherits permissions from the groups it is a member of. This process is called authorization. After authorization, the user can perform specified operations on AOM.

AOM is a project-level service deployed and accessed in specific physical regions. To assign AOM permissions to a user group, specify the scope as region-specific projects and select projects for the permissions to take effect. If **All projects** is selected, the permissions will take effect for the user group in all region-specific projects. When accessing AOM, the users need to switch to a region where they have been authorized to use this service.

You can grant users permissions by using roles and policies.

-  Roles: A coarse-grained authorization mechanism provided by IAM to define permissions based on users' job responsibilities. This mechanism provides only a limited number of service-level roles for authorization. Cloud services depend on each other. When using roles to grant permissions, you may also need to assign other roles on which the permissions depend to take effect. However, roles are not an ideal choice for fine-grained authorization and secure access control.
-  Policies: A type of fine-grained authorization mechanism that defines permissions required to perform operations on specific cloud resources under certain conditions. This mechanism allows for more flexible policy-based authorization, meeting requirements for secure access control. For example, you can grant Elastic Cloud Server (ECS) users only the permissions for managing a certain type of ECSs. Most policies define permissions based on APIs.

:ref:`Table 1 <aom_01_0019__en-us_topic_0000002009339376_table145316572518>` lists all the system permissions supported by AOM.

.. _aom_01_0019__en-us_topic_0000002009339376_table145316572518:

.. table:: **Table 1** System permissions supported by AOM

   +-----------------------------------------+-------------+-------------------------------------------------------------------------------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Subservice Name                         | Policy Name | Description                                                                                     | Type                  | Dependency Permissions                                                                                                                                                                                                                                                                                                              |
   +=========================================+=============+=================================================================================================+=======================+=====================================================================================================================================================================================================================================================================================================================================+
   | Monitoring center/collection management | AOM Admin   | Administrator permissions for AOM 2.0. Users granted these permissions can operate and use AOM. | System-defined policy | CCE FullAccess, DMS ReadOnlyAccess, CCE Namespace-level Permissions, LTS FullAccess                                                                                                                                                                                                                                                 |
   |                                         |             |                                                                                                 |                       |                                                                                                                                                                                                                                                                                                                                     |
   |                                         |             |                                                                                                 |                       | **For CCE namespaces, users or user groups must be granted the administrator (cluster-admin) or custom permissions. If custom permissions are granted, the get, list, and update permissions must be included and the resources of configmaps, prometheuses, servicemonitors, podmonitors, and namespaces must also be specified.** |
   +-----------------------------------------+-------------+-------------------------------------------------------------------------------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   |                                         | AOM Viewer  | Read-only permissions for AOM 2.0. Users granted these permissions can only view AOM data.      | System-defined policy | CCE ReadOnlyAccess, DMS ReadOnlyAccess, CCE Namespace-level Permissions, LTS ReadOnlyAccess                                                                                                                                                                                                                                         |
   |                                         |             |                                                                                                 |                       |                                                                                                                                                                                                                                                                                                                                     |
   |                                         |             |                                                                                                 |                       | **For CCE namespaces, users or user groups must be granted the administrator (cluster-admin) or custom permissions. If custom permissions are granted, the get and list permissions must be included and the resources of configmaps, prometheuses, servicemonitors, podmonitors, and namespaces must also be specified.**          |
   +-----------------------------------------+-------------+-------------------------------------------------------------------------------------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Common Operations and System Permissions for Resource Monitoring
----------------------------------------------------------------

:ref:`Table 2 <aom_01_0019__en-us_topic_0000002009339376_table126113571055>` lists the common operations supported by each system-defined policy of resource monitoring. Select policies as required.

.. _aom_01_0019__en-us_topic_0000002009339376_table126113571055:

.. table:: **Table 2** Common operations supported by each system-defined policy

   ======================================= ========= ==========
   Operation                               AOM Admin AOM Viewer
   ======================================= ========= ==========
   Creating an alarm rule                  Y         x
   Modifying an alarm rule                 Y         x
   Deleting an alarm rule                  Y         x
   Creating an alarm template              Y         x
   Modifying an alarm template             Y         x
   Deleting an alarm template              Y         x
   Creating an alarm notification rule     Y         x
   Modifying an alarm notification rule    Y         x
   Deleting an alarm notification rule     Y         x
   Creating a message template             Y         x
   Modifying a message template            Y         x
   Deleting a message template             Y         x
   Creating a grouping rule                Y         x
   Modifying a grouping rule               Y         x
   Deleting a grouping rule                Y         x
   Creating a suppression rule             Y         x
   Modifying a suppression rule            Y         x
   Deleting a suppression rule             Y         x
   Creating a silence rule                 Y         x
   Modifying a silence rule                Y         x
   Deleting a silence rule                 Y         x
   Creating a dashboard                    Y         x
   Modifying a dashboard                   Y         x
   Deleting a dashboard                    Y         x
   Creating a Prometheus instance          Y         x
   Modifying a Prometheus instance         Y         x
   Deleting a Prometheus instance          Y         x
   Creating an application discovery rule  Y         x
   Modifying an application discovery rule Y         x
   Deleting an application discovery rule  Y         x
   Subscribing to threshold alarms         Y         x
   Configuring a VM log collection path    Y         x
   ======================================= ========= ==========

Common Operations Supported by Each System-defined Policy of Collection Management
----------------------------------------------------------------------------------

:ref:`Table 3 <aom_01_0019__en-us_topic_0000002009339376_table134007221432>` lists the common operations supported by each system-defined policy of collection management. Select policies as required.

.. _aom_01_0019__en-us_topic_0000002009339376_table134007221432:

.. table:: **Table 3** Common operations supported by each system-defined policy of collection management

   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Operation                                                                               | AOM Admin | AOM Viewer |
   +=========================================================================================+===========+============+
   | Querying a proxy area                                                                   | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Editing a proxy area                                                                    | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Deleting a proxy area                                                                   | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Creating a proxy area                                                                   | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying all proxies in a proxy area                                                    | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying all proxy areas                                                                | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying the Agent installation result                                                  | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Obtaining the Agent installation command of a host                                      | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Obtaining the host heartbeat and checking whether the host is connected with the server | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Uninstalling running Agents in batches                                                  | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying the Agent home page                                                            | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Testing the connectivity between the installation host and the target host              | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Installing Agents in batches                                                            | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Obtaining the latest operation log of the Agent                                         | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Obtaining the list of versions that can be selected during Agent installation           | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Obtaining the list of all Agent versions under the current project ID                   | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Deleting hosts with Agents installed                                                    | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying Agent information based on the ECS ID                                          | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Deleting a host with an Agent installed                                                 | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Setting an installation host                                                            | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Resetting installation host parameters                                                  | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying the list of hosts that can be set to installation hosts                        | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying the list of Agent installation hosts                                           | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Deleting an installation host                                                           | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Upgrading Agents in batches                                                             | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying historical task logs                                                           | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying historical task details                                                        | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying all historical tasks                                                           | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying all execution statuses and task types                                          | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying the Agent execution statuses in historical task details                        | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Modifying a proxy                                                                       | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Deleting a proxy                                                                        | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Setting a proxy                                                                         | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying the list of hosts that can be set to proxies                                   | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Updating plug-ins in batches                                                            | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Uninstalling plug-ins in batches                                                        | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Installing plug-ins in batches                                                          | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying historical task logs of a plug-in                                              | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying all plug-in execution records                                                  | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying plug-in execution records based on the task ID                                 | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying the plug-in execution statuses in historical task details                      | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Obtaining the plug-in list                                                              | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying the plug-in version                                                            | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Querying the list of supported plug-ins                                                 | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Obtaining the CCE cluster list                                                          | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Obtaining the Agent list of a CCE cluster                                               | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Installing ICAgent on a CCE cluster                                                     | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Upgrading ICAgent for a CCE cluster                                                     | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Uninstalling ICAgent from a CCE cluster                                                 | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Obtaining the CCE cluster list                                                          | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Obtaining the list of hosts where the ICAgent has been installed                        | Y         | Y          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Installing ICAgent on CCE cluster hosts                                                 | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Upgrading ICAgent on CCE cluster hosts                                                  | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+
   | Uninstalling ICAgent from CCE cluster hosts                                             | Y         | x          |
   +-----------------------------------------------------------------------------------------+-----------+------------+

Fine-grained Permissions
------------------------

To use a custom fine-grained policy, log in to IAM as the administrator and select fine-grained permissions of AOM as required. For details about fine-grained permissions of AOM, see :ref:`Table 4 <aom_01_0019__en-us_topic_0000002009339376_table13611192118526>`.

.. _aom_01_0019__en-us_topic_0000002009339376_table13611192118526:

.. table:: **Table 4** Fine-grained permissions of AOM

   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | Permission                 | Description                                 | Permission Dependency | Application Scenario                                                      |
   +============================+=============================================+=======================+===========================================================================+
   | aom:alarm:put              | Reporting an alarm                          | N/A                   | Reporting a custom alarm                                                  |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:event2AlarmRule:create | Adding an event alarm rule                  |                       | Adding an event alarm rule                                                |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:event2AlarmRule:set    | Modifying an event alarm rule               |                       | Modifying an event alarm rule                                             |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:event2AlarmRule:delete | Deleting an event alarm rule                |                       | Deleting an event alarm rule                                              |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:event2AlarmRule:list   | Querying all event alarm rules              |                       | Querying all event alarm rules                                            |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:actionRule:create      | Adding an alarm notification rule           |                       | Adding an alarm notification rule                                         |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:actionRule:delete      | Deleting an alarm notification rule         |                       | Deleting an alarm notification rule                                       |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:actionRule:list        | Querying the alarm notification rule list   |                       | Querying the alarm notification rule list                                 |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:actionRule:update      | Modifying an alarm notification rule        |                       | Modifying an alarm notification rule                                      |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:actionRule:get         | Querying an alarm notification rule by name |                       | Querying an alarm notification rule by name                               |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:alarm:list             | Obtaining the sent alarm content            |                       | Obtaining the sent alarm content                                          |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:alarmRule:create       | Creating a threshold rule                   |                       | Creating a threshold rule                                                 |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:alarmRule:set          | Modifying a threshold rule                  |                       | Modifying a threshold rule                                                |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:alarmRule:get          | Querying threshold rules                    |                       | Querying all threshold rules or a single threshold rule by rule ID        |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:alarmRule:delete       | Deleting a threshold rule                   |                       | Deleting threshold rules in batches or a single threshold rule by rule ID |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:discoveryRule:list     | Querying application discovery rules        |                       | Querying existing application discovery rules                             |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:discoveryRule:delete   | Deleting an application discovery rule      |                       | Deleting an application discovery rule                                    |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:discoveryRule:set      | Adding an application discovery rule        |                       | Adding an application discovery rule                                      |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:metric:list            | Querying time series objects                |                       | Querying time series objects                                              |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:metric:list            | Querying time series data                   |                       | Querying time series data                                                 |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:metric:get             | Querying metrics                            |                       | Querying metrics                                                          |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:metric:get             | Querying monitoring data                    |                       | Querying monitoring data                                                  |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:muteRule:delete        | Deleting a silence rule                     | N/A                   | Deleting a silence rule                                                   |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:muteRule:create        | Adding a silence rule                       |                       | Adding a silence rule                                                     |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:muteRule:update        | Modifying a silence rule                    |                       | Modifying a silence rule                                                  |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+
   | aom:muteRule:list          | Querying the silence rule list              |                       | Querying the silence rule list                                            |
   +----------------------------+---------------------------------------------+-----------------------+---------------------------------------------------------------------------+

Roles/Policies Required by AOM Dependency Services
--------------------------------------------------

If an IAM user needs to view data or use functions on the AOM console, grant the **AOM Admin** or **AOM Viewer** policy to the user group to which the user belongs and then add the roles or policies required by dependency services by referring to :ref:`Table 5 <aom_01_0019__en-us_topic_0000002009339376_table144002293016>`. **When you subscribe to AOM for the first time, AOM will automatically create a service agency. In addition to the** **AOM Admin** **permission, the** **Security Administrator** **permission must be granted.**

.. _aom_01_0019__en-us_topic_0000002009339376_table144002293016:

.. table:: **Table 5** Roles/Policies required by AOM dependency services

   +--------------------------+---------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Console Function         | Dependency Service                          | Policy/Role Required                                                                                                                                                                                      |
   +==========================+=============================================+===========================================================================================================================================================================================================+
   | -  Workload monitoring   | CCE                                         | To use workload and cluster monitoring and Prometheus for CCE, you need to set the **CCE FullAccess** and :ref:`CCE Namespace <aom_01_0019__en-us_topic_0000002009339376_table145316572518>` permissions. |
   | -  Cluster monitoring    |                                             |                                                                                                                                                                                                           |
   | -  Prometheus for CCE    |                                             |                                                                                                                                                                                                           |
   +--------------------------+---------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | -  Log management        | LTS                                         | To use log management, log transfer, log ingestion rules, host group management, and log alarm rules, you need to set the **LTS FullAccess** permission.                                                  |
   | -  Log transfer          |                                             |                                                                                                                                                                                                           |
   | -  Log ingestion rules   |                                             |                                                                                                                                                                                                           |
   | -  Host group management |                                             |                                                                                                                                                                                                           |
   | -  Log alarm rules       |                                             |                                                                                                                                                                                                           |
   +--------------------------+---------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
   | Enterprise project       | Enterprise Project Management Service (EPS) | To use enterprise projects, you need to set the **EPS ReadOnlyAccess** permission.                                                                                                                        |
   +--------------------------+---------------------------------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
