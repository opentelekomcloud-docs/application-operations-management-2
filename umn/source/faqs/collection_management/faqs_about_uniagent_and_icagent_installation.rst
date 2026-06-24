:original_name: aom_06_0025.html

.. _aom_06_0025:

FAQs About UniAgent and ICAgent Installation
============================================

#. What Can I Do If the Network Between the UniAgent Installation Host and Target Host Is Disconnected ("[warn] ssh connect failed, 1.2.1.2:22")?

   Check network connectivity before installing an Agent, and select an installation host that is accessible from the Internet.

#. What Can I Do If the Heartbeat Detection and Registration Fail and the Network Is Disconnected After I Install a UniAgent?

   Run the **telnet** *proxy IP address* command on the target host to check whether the network between the proxy and target host is normal.

#. Ports 8149, 8102, 8923, 30200, 30201, and 80 need to be enabled during ICAgent installation. Can port 80 be disabled after ICAgent is installed?

   Port 80 is used only for pulling Kubernetes software packages. You can disable it after installing the ICAgent.

#. Will the ICAgent installed in a Kubernetes cluster be affected after the cluster version is upgraded?

   After the cluster version is upgraded, the system will restart the ICAgent and upgrade it to the latest version.
