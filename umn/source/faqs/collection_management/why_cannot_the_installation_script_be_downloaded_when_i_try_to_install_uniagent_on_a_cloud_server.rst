:original_name: aom_06_0063.html

.. _aom_06_0063:

Why Cannot the Installation Script Be Downloaded When I Try to Install UniAgent on a Cloud Server?
==================================================================================================

Symptom
-------

During UniAgent installation on a cloud server, the installation script cannot be downloaded. Message "Could not resolve host: aom-uniagent-*xxxxxxxxxxxxxxxxxxxxxxxxxxxx*" is displayed.


.. figure:: /_static/images/en-us_image_0000002370948721.png
   :alt: **Figure 1** Error information

   **Figure 1** Error information

Possible Cause
--------------

The host cannot resolve the Object Storage Service (OBS) domain name.

Solution
--------

Add Domain Name Service (DNS) server addresses for the ECS running Linux and then add a security group.

You can add DNS server addresses for the ECS by running commands or through the management console.

-  To add DNS server addresses by running commands, perform the following steps:

   #. Log in to the ECS as user **root**.

   #. Run the **vi /etc/resolv.conf** command to open the file.

   #. .. _aom_06_0063__li17315192175112:

      Add **nameserver xx.xx.xx** to the file.

      *xx.xx.xx* indicates private DNS server addresses.

   #. Enter **:wq** and press **Enter** to save the settings and exit.

-  To add DNS server addresses for the ECS through the management console, perform the following steps:

   #. In the upper left corner of the management console, select a target region and project.

   #. Click **Service List** in the upper left corner. Under **Compute**, select **Elastic Cloud Server**.

   #. In the ECS list, click the ECS name to go to the ECS details page.

   #. In the **Summary** tab page, click the VPC name.

      The **Virtual Private Cloud** page is displayed.

   #. In the VPC list, locate the target VPC and click its name.

   #. In the **Networking Components** area, click the number following **Subnets**.

      The **Subnets** page is displayed.

   #. In the subnet list, locate the target subnet and click its name.

   #. In the **Gateway and DNS Information** area, click |image1| following **DNS Server Address**.

      .. note::

         Set the DNS server address to the value of **nameserver** in :ref:`3 <aom_06_0063__li17315192175112>`.

   #. Click **OK**.

      .. note::

         The new DNS server address takes effect after the ECS is restarted.

-  To add a security group through the management console, perform the following steps:

   #. In the upper left corner of the management console, select a target region and project.

   #. Click **Service List** in the upper left corner. Under **Compute**, select **Elastic Cloud Server**.

   #. In the ECS list, click the ECS name to go to the ECS details page.

   #. On the **Security Groups** tab page, click a security group name. The security group details page is displayed.

   #. Go to the **Outbound Rules** tab page and then click **Add Rule**.

      Add a rule by referring to :ref:`Table 1 <aom_06_0063__table168311845185818>`.

      .. _aom_06_0063__table168311845185818:

      .. table:: **Table 1** Parameters for adding a security group rule

         +----------+--------+------+-----------------+-----+----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Priority | Action | Type | Protocol & Port |     | Destination    | Description                                                                                                                                                          |
         +==========+========+======+=================+=====+================+======================================================================================================================================================================+
         | 1        | Allow  | IPv4 | TCP             | 80  | 100.125.0.0/16 | Used to download the UniAgent installation package from the OBS bucket to the ECS and obtain the metadata and authentication information of the ECS.                 |
         +----------+--------+------+-----------------+-----+----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | 1        | Allow  | IPv4 | TCP and UDP     | 53  | 100.125.0.0/16 | Used by DNS to resolve domain names, for example, resolve the OBS domain name when you download the UniAgent installation package, and resolve the UniAgent address. |
         +----------+--------+------+-----------------+-----+----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | 1        | Allow  | IPv4 | TCP             | 443 | 100.125.0.0/16 | Used to collect monitoring data and report them to AOM.                                                                                                              |
         +----------+--------+------+-----------------+-----+----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------+

.. |image1| image:: /_static/images/en-us_image_0000002371028873.png
