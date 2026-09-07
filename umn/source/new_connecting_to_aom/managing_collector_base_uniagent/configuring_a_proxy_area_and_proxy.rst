:original_name: uiagent_01_0010.html

.. _uiagent_01_0010:

Configuring a Proxy Area and Proxy
==================================

To enable network communication between multiple clouds, you need to configure an ECS as a proxy. The target host forwards O&M data to AOM through the proxy. A proxy area is used to manage proxies by category. It consists of multiple proxies.

Procedure
---------

#. Log in to the AOM 2.0 console.

#. In the navigation pane on the left, choose **Settings** > **Global Settings**.

#. In the navigation pane, choose **Collection Settings** > **Proxy Areas**.

#. Click **Add Proxy Area** and set proxy area parameters.

   .. table:: **Table 1** Proxy area parameters

      =============== ============================== =======
      Parameter       Description                    Example
      =============== ============================== =======
      Proxy Area Name Name of a proxy area. Max.: 64 test
      =============== ============================== =======

#. .. _uiagent_01_0010__agent_01_0010_li1258912141089:

   Click **OK** to add a proxy area.

#. Locate the new proxy area, click **Add Proxy**, and set proxy parameters.

   .. table:: **Table 2** Proxy parameters

      +-----------------------+--------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                            | Example               |
      +=======================+========================================================================================================+=======================+
      | Proxy Area            | Select a :ref:`proxy area <uiagent_01_0010__agent_01_0010_li1258912141089>` that you have created.     | test                  |
      +-----------------------+--------------------------------------------------------------------------------------------------------+-----------------------+
      | Host                  | Select a host where the UniAgent has been installed. Hosts running Windows cannot be added as proxies. | ``-``                 |
      +-----------------------+--------------------------------------------------------------------------------------------------------+-----------------------+
      | Proxy IP Address      | Set the IP address of the proxy.                                                                       | 192.168.0.0           |
      +-----------------------+--------------------------------------------------------------------------------------------------------+-----------------------+
      | Port                  | Set a port number and proxy protocol.                                                                  | 32555                 |
      |                       |                                                                                                        |                       |
      |                       | -  The default port number is **32555**. Range: 1,025 to 65,535.                                       |                       |
      |                       | -  The proxy protocol can only be **SOCKS5**.                                                          |                       |
      +-----------------------+--------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **OK**.

   After configuring the proxy area and proxy, perform the following operations if needed:

   .. table:: **Table 3** Managing the proxy area and proxy

      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Operation                    | Description                                                                                                                                        |
      +==============================+====================================================================================================================================================+
      | Searching for a proxy area   | Click |image4| next to **Add Proxy Area**. Then, in the search box, enter a keyword to search for your target proxy area.                          |
      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Modifying a proxy area       | Hover the pointer over a proxy area and choose |image5| > **Edit**. In the dialog box that is displayed, enter a new name, and click **OK**.       |
      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Deleting a proxy area        | Hover the pointer over a proxy area and choose |image6| > **Delete**. In the dialog box that is displayed, click **Yes** to delete the proxy area. |
      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Checking a proxy             | Click a proxy area to check the proxy in it.                                                                                                       |
      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Modifying a proxy IP address | Click **Modify Proxy IP** in the **Operation** column of the proxy. On the page that is displayed, modify the proxy IP address.                    |
      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+
      | Deleting a proxy             | Click **Delete** in the **Operation** column of the proxy. In the displayed dialog box, click **Yes** to delete the proxy.                         |
      +------------------------------+----------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002336871100.png
.. |image2| image:: /_static/images/en-us_image_0000002336871096.png
.. |image3| image:: /_static/images/en-us_image_0000002337030856.png
.. |image4| image:: /_static/images/en-us_image_0000002336871100.png
.. |image5| image:: /_static/images/en-us_image_0000002336871096.png
.. |image6| image:: /_static/images/en-us_image_0000002337030856.png
