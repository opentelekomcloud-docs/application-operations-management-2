:original_name: mon_01_0044.html

.. _mon_01_0044:

Alarm Tags and Annotations
==========================

When creating alarm rules, you can set alarm rule tags and annotations. Tags are attributes that can be used to identify alarms. They are used in alarm noise reduction scenarios. Annotations are attributes that cannot be used to identify alarms. They are used in scenarios such as alarm notification and message templates.

Alarm Rule Tag Description
--------------------------

-  Alarm rule tags can apply to grouping rules, suppression rules, and silence rules. The alarm management system manages alarms and notifications based on the tags.
-  Each tag is in "key:value" format and can be customized. You can create a maximum of 20 custom tags. Each key and value can contain only letters, digits, and underscores (_).
-  If you set a tag when creating an alarm rule, the tag is automatically added as an alarm attribute when an alarm is triggered.
-  In a message template, the **$event.metadata.key1** variable specifies a tag. For details, see :ref:`Table 2 <mon_01_0016__table12639440194518>`.

Alarm Rule Annotation Description
---------------------------------

-  Annotations are attributes that cannot be used to identify alarms. They are used in scenarios such as alarm notification and message templates.
-  Each annotation is in "key:value" format and can be customized. You can create a maximum of 20 custom annotations. Each key and value can contain only letters, digits, and underscores (_).
-  In a message template, the **$event.annotations.key2** variable specifies an annotation. For details, see :ref:`Table 2 <mon_01_0016__table12639440194518>`.

Managing Alarm Rule Tags and Annotations
----------------------------------------

You can add, delete, modify, and query alarm tags or annotations on the alarm rule page.

#. Log in to the AOM 2.0 console.
#. In the navigation pane, choose **Alarm Center** > **Alarm Rules**.
#. Click **Create Alarm Rule**, or locate a desired alarm rule and click |image1| in the **Operation** column.
#. On the displayed page, click **Advanced Settings**.
#. Under **Alarm Rule Tag** or **Alarm Rule Annotation**, click |image2| and enter a key and value.
#. Click **OK** to add an alarm rule tag or annotation.

   -  Adding multiple alarm rule tags or annotations: Click |image3| multiple times to add alarm rule tags or annotations (max.: 20).
   -  Modifying an alarm rule tag or annotation: Move the cursor to a desired alarm rule tag or annotation and click |image4| to modify them.
   -  Deleting an alarm rule tag or annotation: Move the cursor to a desired alarm rule tag or annotation and click |image5| to delete them.

.. |image1| image:: /_static/images/en-us_image_0000002370949957.png
.. |image2| image:: /_static/images/en-us_image_0000002336872016.png
.. |image3| image:: /_static/images/en-us_image_0000002371030129.png
.. |image4| image:: /_static/images/en-us_image_0000002371030117.png
.. |image5| image:: /_static/images/en-us_image_0000002336872000.png
