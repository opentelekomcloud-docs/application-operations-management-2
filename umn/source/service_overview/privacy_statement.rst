:original_name: aom_01_0035.html

.. _aom_01_0035:

Privacy Statement
=================

All O&M data will be displayed on the AOM console. Therefore, do not upload your privacy or sensitive data to AOM. If necessary, encrypt such data.

Collector Deployment
--------------------

During the installation of UniAgent and ICAgent on Linux hosts, the history recording function is disabled. Therefore, your AK/SK and access code cannot be viewed by running commands. Additionally, credentials are encrypted for storage to prevent leaks.

Container Monitoring
--------------------

For Cloud Container Engine (CCE) container monitoring, the AOM collector (ICAgent) must run as a privileged container. Evaluate the security risks of the privileged container and identify your container service scenarios. For example, for a node that provides services through logical multi-tenant container sharing, use open-source tools such as Prometheus to monitor the services and do not use ICAgent.
