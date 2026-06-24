:original_name: mon_01_0056.html

.. _mon_01_0056:

Authorizing AOM to Access Other Cloud Services
==============================================

Grant permissions to access Resource Management Service (RMS), Log Tank Service (LTS), Cloud Container Engine (CCE), Cloud Container Instance (CCI), Cloud Eye, Distributed Message Service (DMS), and Elastic Cloud Server (ECS). The permission setting takes effect for the entire AOM 2.0 service.

Prerequisites
-------------

You have been granted the **AOM Admin** and **Security Administrator** permissions.


Authorizing AOM to Access Other Cloud Services
----------------------------------------------

#. Log in to the AOM 2.0 console.

#. In the navigation pane, choose **Settings** > **Global Settings**. The **Global Settings** page is displayed.

#. In the upper right corner of the cloud service authorization page, click **Authorize** to grant permissions to access the preceding cloud services with one click.

   Upon authorization, the **aom_admin_trust** agency will be created in IAM.

   -  If **Cancel Authorization** is displayed in the upper right corner of the page, you already have the permissions to access the preceding cloud services.
   -  To cancel authorization, click **Cancel Authorization**.
