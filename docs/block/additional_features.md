# Additional Features
In the additional features you can configure the access to Opencast Studio, the visibility of episodes, the activity module settings as well as some other features.

## Settings for the chunkuploader
If you also have the chunkuploader installed you configure it in this section.

* **Enable Chunkupload:** If Chunkupload is enabled it will be possible to upload videos using the chunkupload plugin. Defaults to yes.
* **Video size limit:** Limit the file size of uploaded videos through the chunkupload. The default is 2GB.

## Opencast studio integration
In this section you can enable the feature to add [Opencast Studio](https://docs.opencast.org/develop/admin/#modules/studio/) support to the block. For this to work Opencast Studio needs to be running on the admin node and [LTI](https://docs.opencast.org/develop/admin/#modules/ltimodule/) needs to be enabled. Furthermore LTI users need to be allowed to access Opencast Studio, for this they need the additional role ´ROLE_STUDIO´. The options are:

* **Show the link to opencast studio:** This option renders a button to opencast studio in the block content and the block overview. Opencast studio has to run on your opencast admin node and the following LTI settings have to be configured as well. Defaults to no.
* **Consumer key:** LTI Consumer key for the opencast studio integration.
* **Consumer secret:** LTI Consumer secret for the opencast studio integration.

**Recommendation:** It is possible to configure Opencast Studio to add certain ACLs to the recorded videos. It is recommended to add the same ACLs to recorded videos as to uploaded videos via the block.

## Control episode visibility
In this section you can configure if the teacher is allowed to control the visibility of an Opencast episode after the episode has been processed. The options are:

* **Allow episode visibility control after processing:** If enabled, teachers can control the visibility of an Opencast episode after the episode has been processed in Opencast. Defaults to yes.
* **Allow episode group restriction:** If enabled, teachers can not only control the visibility of an Opencast episode for all course users but can also restrict the visibility to particular course groups. Defaults to yes.

## Opencast activity modules
If you also have the Opencast Video Provider activity installed, you can configure it in this section.

* **Enable Opencast activity:** If enabled, teachers can add an activity for the series to the course.
* **Default activity title:** Default title that is used when a new Opencast activity is added to a course.
* **Add series module intro:** If enabled, teachers can add a description to the Opencast activity series module that is shown on the course overview page.
* **Choose series module section:** If enabled, teachers can choose the section which the Opencast Activity series module will be added to.
* **Set series module availability:** If enabled, teachers can set the availability conditions when a new Opencast LTI series module is added to a course.
* **Enable Opencast activity for episodes:** If enabled, teachers can add activities for episodes to the course.
* **Add episode module intro:** If enabled, teachers can add a description to the Opencast activity episode module that is shown on the course overview page.
* **Choose episode module section:** If enabled, teachers can choose the section which the Opencast Activity episode module will be added to.
* **Set episode module availability:** If enabled, teachers can set the availability conditions when a new Opencast Activity episode module is added to a course.

For the availability features, the *Enable restricted access* feature must be activated in the global settings.

## Additional features
In this section, unrelated configurations are collected.

* **Download channel:** If not empty, teachers can download processed videos. The video files are served from the specified Opencast channel.
* **Workflow tag:** Tag for Opencast workflow definitions that can be configured by the administrator and manually started by teachers.
* **Support email:** If not empty, teachers can report problems for their uploaded videos. An email with technical information as well as a message entered by the teachers is sent to this support email address.
* **Terms of use:** If not empty, a checkbox with the terms of use will appear on the "Video upload" page. Teachers must accept the entered terms of use before they can upload a video.