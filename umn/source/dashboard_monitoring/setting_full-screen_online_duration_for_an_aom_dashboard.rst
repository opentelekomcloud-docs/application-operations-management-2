:original_name: mon_01_0041.html

.. _mon_01_0041:

Setting Full-Screen Online Duration for an AOM Dashboard
========================================================

When an AOM dashboard is used for monitoring in full-screen mode, the full-screen mode will exit when your account logs out. As a result, real-time monitoring cannot be performed. To prevent this, AOM allows you to customize full-screen online duration.

Constraints
-----------

-  For security purposes, exit the full-screen view when it is not required.

-  The full-screen online duration is irrelevant to operations. If the preset duration times out, the login page is automatically displayed.

-  The full-screen online duration takes precedence over the automatic logout mechanism of the cloud.

   For example, if you log in to the console, set the full-screen online duration to 2 hours on AOM pages, and then open other pages, your setting on the AOM pages also takes effect on other pages. That is, the login page will be automatically displayed 2 hours later.

-  If you leave all full-screen views, the default automatic logout mechanism is used.

   For example, if you log in to the console, set the full-screen online duration to 2 hours on AOM pages, open other pages, and then leave all full-screen views of AOM, the default logout mechanism will be used. That is, if you do not perform any operations within 1 hour, the login page will be automatically displayed.

Procedure
---------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Dashboard** > **Dashboard**. If you want to use new dashboards, choose **Dashboard** in the navigation pane and then click **Try New Version** in the upper right corner of the page.

#. Click a target dashboard and click |image1| in the upper right corner of the dashboard details page.

#. In the dialogue box that is displayed, set the full-screen online duration. For details, see :ref:`Table 1 <mon_01_0041__table2466533131215>`.


   .. figure:: /_static/images/en-us_image_0000002371030253.png
      :alt: **Figure 1** Setting the online duration

      **Figure 1** Setting the online duration

   .. _mon_01_0041__table2466533131215:

   .. table:: **Table 1** Online duration parameters

      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                         | Description                                                                                                                                                                   |
      +===================================+===============================================================================================================================================================================+
      | Online Setting                    | Mode of setting the online duration. Options:                                                                                                                                 |
      |                                   |                                                                                                                                                                               |
      |                                   | -  **Custom**: After the specified duration expires, the login page will be automatically displayed.                                                                          |
      |                                   | -  **Always online**: The full-screen online duration is not restricted. That is, you can always implement full-screen monitoring and the login page will never be displayed. |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Duration                          | Full-screen online duration. The duration varies according to the setting mode.                                                                                               |
      |                                   |                                                                                                                                                                               |
      |                                   | -  **Custom**: The default duration is 1 hour. Range: 1 to 24 hours.                                                                                                          |
      |                                   |                                                                                                                                                                               |
      |                                   |    For example, if you enter **2** in the text box, the login page will be automatically displayed 2 hours later.                                                             |
      |                                   |                                                                                                                                                                               |
      |                                   | -  **Always online**: The default value is **Always online** and cannot be changed.                                                                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Dashboard Rotation                | Specifies whether to enable dashboard rotation. If this function is enabled, you need to set **Rotation Period** and **Dashboard**.                                           |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Rotation Period                   | Period for rotating dashboards. Range: 10s to 120s. Default: 10s.                                                                                                             |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Dashboard                         | Dashboard to be rotated. Select one or more dashboards from the drop-down list.                                                                                               |
      +-----------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

#. Click **OK** to enter the full-screen mode.

.. |image1| image:: /_static/images/en-us_image_0000002370950089.png
