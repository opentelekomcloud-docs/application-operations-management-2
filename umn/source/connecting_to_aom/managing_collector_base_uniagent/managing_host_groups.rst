:original_name: agent_01_0020.html

.. _agent_01_0020:

Managing Host Groups
====================

AOM is a unified platform for observability analysis. It does not provide log functions by itself. Instead, it integrates the host group management function of Log Tank Service (LTS). You can perform operations on the AOM 2.0 or LTS console.

To use the host group management function on the AOM 2.0 console, enable LTS first.

.. table:: **Table 1** Description

   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+
   | Function              | Description                                                                                                                                                                                                                                                         | AOM 2.0 Console                                                                                    | LTS Console                                            | References                                                                                |
   +=======================+=====================================================================================================================================================================================================================================================================+====================================================================================================+========================================================+===========================================================================================+
   | Host group management | Host groups allow you to configure host log ingestion efficiently. You can add multiple hosts to a host group and associate the host group with log ingestion configurations. The ingestion configurations will then be applied to all the hosts in the host group. | #. Log in to the AOM 2.0 console.                                                                  | #. Log in to the LTS console.                          | `Managing Host Groups <https://docs.otc.t-systems.com/usermanual/lts/lts_02_1033.html>`__ |
   |                       |                                                                                                                                                                                                                                                                     | #. In the navigation pane, choose **Settings** > **Global Settings**.                              | #. In the navigation pane, choose **Host Management**. |                                                                                           |
   |                       |                                                                                                                                                                                                                                                                     | #. On the displayed page, choose **Collection Settings** > **Host Groups** in the navigation pane. |                                                        |                                                                                           |
   +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+----------------------------------------------------------------------------------------------------+--------------------------------------------------------+-------------------------------------------------------------------------------------------+

-  To use LTS functions on the AOM console, you need to obtain LTS permissions in advance.
-  AOM 2.0 also provides a new version of host group management. After you switch to the new access center, the :ref:`new host group management <agent_02_1033>` page will be displayed.
