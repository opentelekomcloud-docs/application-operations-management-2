:original_name: mon_01_0086.html

.. _mon_01_0086:

Using AOM to Monitor Component Processes
========================================

Components refer to the services that you deploy, including containers and common processes. The component list displays the name, running status, and application of each component. AOM supports drill-down from a component to an instance, and then to a process. By viewing the status of each layer, you can implement dimensional monitoring for components.

Constraints
-----------

-  A maximum of five tags can be created for each component.

   -  Tag key: max. 36 characters; tag value: max. 43 characters
   -  A tag value can contain only letters, digits, hyphens (-), and underscores (_).

-  Components cannot be filtered by alias.

Procedure
---------

#. Log in to the AOM 2.0 console.
#. In the navigation pane, choose **Infrastructure Monitoring** > **Process Monitoring**. Next, click the **Component Monitoring** tab. Then you can view the component list.

   -  The component list displays information such as **Component Name**, **Application**, **Deployment Mode**, and **Application Discovery Rules**.
   -  To view target components, you can set filter criteria (such as the running status, application, cluster name, deployment mode, and component name) above the component list.
   -  Enable or disable **Hide System Components** as required. By default, system components are hidden.
   -  Click |image1| in the upper right corner of the page and select or deselect the columns to display.

#. Click |image2| in the upper right corner of the page and select a desired value from the drop-down list.

   a. Set a time range to view components. There are two methods to set a time range:

      Method 1: Use a predefined time label, such as **Last 30 minutes** or **Last hour** in the upper right corner of the page. You can select a time range as required.

      Method 2: Specify the start time and end time to customize a time range. You can specify 30 days at most.

   b. Set the interval for refreshing information. Click |image3| and select a value from the drop-down list, such as **Refresh manually** or **1 minute auto refresh**.

#. Perform the following operations if needed:

   -  **Adding an alias**

      If a component name is complex to identify, you can add an alias for the component.

      In the component list, click |image4| in the **Operation** column of the target component, enter an alias, and click **OK**. The added alias can be modified but cannot be deleted.

   -  **Adding a tag**

      Tags are identifiers of components. You can distinguish system components from non-system components based on tags. By default, AOM adds the **System Service** tag to system components (including icagent, css-defender, nvidia-driver-installer, nvidia-gpu-device-plugin, kube-dns, org.tanukisoftware.wrapper.WrapperSimpleApp, evs-driver, obs-driver, sfs-driver, icwatchdog, and sh).

      In the component list, click |image5| in the **Operation** column of the target component. In the displayed dialog box, enter a tag key and value, click |image6|, select the **Mark as system component** check box, and click **OK**.

#. Set filter criteria to search for the desired component.
#. Click the component name. The component details page is displayed.

   -  On the **Instance List** tab page, view the instance details. Click an instance name to view the monitoring view and alarm information.
   -  On the **Host List** tab page, view the host details.
   -  On the **Monitoring Views** tab page, select a desired Prometheus instance to view the resource usage of the component. Click |image7| in the upper right corner of the page to view resource information in full screen.
   -  On the **Alarms** tab page, view the alarm details of the component. For details, see :ref:`Checking AOM Alarms or Events <mon_01_0011>`.
   -  On the **Events** tab page, view the event details of the component. For details, see :ref:`Checking AOM Alarms or Events <mon_01_0011>`.

.. |image1| image:: /_static/images/en-us_image_0000002336871788.png
.. |image2| image:: /_static/images/en-us_image_0000002337031544.png
.. |image3| image:: /_static/images/en-us_image_0000002370949753.png
.. |image4| image:: /_static/images/en-us_image_0000002370949749.png
.. |image5| image:: /_static/images/en-us_image_0000002336871808.png
.. |image6| image:: /_static/images/en-us_image_0000002337031552.png
.. |image7| image:: /_static/images/en-us_image_0000002336871792.png
