:original_name: mon_01_0110.html

.. _mon_01_0110:

Global Configuration of AOM
===========================

AOM supports the following global configuration:

-  **Metric Collection**: whether to collect metrics (excluding SLA and custom metrics).
-  **TMS Tag Display**: whether to display cloud resource tags in alarm notifications.

Constraints
-----------

-  The global configuration takes effect for the entire AOM 2.0.
-  The **TMS tag: $event.annotations.tms_tags** variable configured in the :ref:`alarm message template <mon_01_0016__section98731914104516>` takes effect only after **TMS Tag Display** is enabled.
-  After metric collection is disabled, ICAgents will stop collecting metrics and related metric data will not be updated. However, custom metrics can still be reported.

.. _mon_01_0110__section633611121560:

Configuring Metric Collection
-----------------------------

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, choose **Settings** > **Global Settings**.
#. On the displayed page, choose **Global Configuration** in the navigation pane. Then enable or disable **Metric Collection** as required.

Configuring TMS Tag Display
---------------------------

#. Log in to the AOM 2.0 console.
#. In the navigation pane on the left, choose **Settings** > **Global Settings**.
#. In the navigation pane on the left, choose **Global Configuration**. Then enable or disable **TMS Tag Display** as required.
