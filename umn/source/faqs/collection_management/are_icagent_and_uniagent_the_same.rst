:original_name: aom_06_0038.html

.. _aom_06_0038:

Are ICAgent and UniAgent the Same?
==================================

ICAgent is a plug-in, but UniAgent is not.

-  UniAgent is an Agent for unified data collection and serves as the base of the cloud service O&M system. It delivers instructions, such as script delivery and execution, and integrates plug-ins (such as ICAgent, Cloud Eye, and Telescope) and maintains their status. UniAgent provides middleware and custom metric collection capabilities.

   .. note::

      UniAgent does not collect O&M data; instead, collection plug-ins do that.

-  ICAgent collects metrics and logs for AOM and LTS.


.. figure:: /_static/images/en-us_image_0000002336870756.png
   :alt: **Figure 1** ICAgent and UniAgent

   **Figure 1** ICAgent and UniAgent
