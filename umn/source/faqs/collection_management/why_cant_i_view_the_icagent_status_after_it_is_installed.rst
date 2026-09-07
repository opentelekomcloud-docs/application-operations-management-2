:original_name: aom_06_0046.html

.. _aom_06_0046:

Why Can't I View the ICAgent Status After It Is Installed?
==========================================================

Symptom
-------

After the ICAgent is installed, its status cannot be viewed on the console.

Possible Cause
--------------

The virtual NIC is used on the user side. To obtain the ICAgent status, modify the script according to the following procedure.

Solution
--------

#. Log in to a host where the ICAgent has been installed as the **root** user.

#. Check the host IP address in use, as shown in :ref:`Figure 1 <aom_06_0046__fig3509748143917>`:

   .. code-block::

      netstat -nap | grep establish -i

   .. _aom_06_0046__fig3509748143917:

   .. figure:: /_static/images/en-us_image_0000002337030508.png
      :alt: **Figure 1** Checking the host IP address

      **Figure 1** Checking the host IP address

#. Check the NIC corresponding to the IP address, as shown in :ref:`Figure 2 <aom_06_0046__fig15215144124216>`:

   .. code-block::

      ifconfig | grep IP address -B1

   .. _aom_06_0046__fig15215144124216:

   .. figure:: /_static/images/en-us_image_0000002336870752.png
      :alt: **Figure 2** Checking the NIC corresponding to the IP address

      **Figure 2** Checking the NIC corresponding to the IP address

#. Go to the **/sys/devices/virtual/net/** directory and check whether the NIC name exists.

   -  If it exists, it is a virtual NIC. Then go to :ref:`5 <aom_06_0046__li10526519184712>`.

   -  If it does not exist, it is not a virtual NIC. Then contact technical support.

#. .. _aom_06_0046__li10526519184712:

   Modify the ICAgent startup script:

   a. Open the **icagent_mgr.sh** file (command varies depending on the ICAgent version):

      .. code-block::

         vi /opt/oss/servicemgr/ICAgent/bin/manual/icagent_mgr.sh

      Or

      .. code-block::

         vi /var/opt/oss/servicemgr/ICAgent/bin/manual/icagent_mgr.sh

   b. Modify the script file:

      Add **export IC_NET_CARD=**\ *NIC name* to the file, as shown in :ref:`Figure 3 <aom_06_0046__fig1831543865817>`.

      .. _aom_06_0046__fig1831543865817:

      .. figure:: /_static/images/en-us_image_0000002370948697.png
         :alt: **Figure 3** Modifying the script

         **Figure 3** Modifying the script

#. Restart the ICAgent (commands vary depending on the ICAgent version):

   .. code-block::

      sh /opt/oss/servicemgr/ICAgent/bin/manual/mstop.sh
      sh /opt/oss/servicemgr/ICAgent/bin/manual/mstart.sh

   Or

   .. code-block::

      sh /opt/oss/servicemgr/ICAgent/bin/manual/mstop.sh
      sh /var/opt/oss/servicemgr/ICAgent/bin/manual/mstop.sh

#. Log in to the AOM console and choose **Settings** > **Global Settings** > **Collection Settings** > **UniAgents** to check whether the ICAgent status is displayed.

   -  If the ICAgent status is displayed, no further action is required.

   -  If the ICAgent status is still not displayed, contact technical support.
