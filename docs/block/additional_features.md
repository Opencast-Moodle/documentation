# Additional Features

In the additional features you can configure the access to Opencast Studio as well as for LTI activities.

## Settings for the chunkuploader

If you also have the chunkuploader installed you configure it in this section.

* **Enable Chunkupload:** If Chunkupload is enabled it will be possible to upload videos using the chunkupload plugin. Defaults to yes.
* **Video size limit:** Limit the file size of uploaded videos through the chunkupload. The default is 2GB.

## Opencast studio

In this section you can enable the feature to add [Opencast Studio](https://docs.opencast.org/develop/admin/#modules/studio/) support to the block. For this to work Opencast Studio needs to be running on the admin node and [LTI](https://docs.opencast.org/develop/admin/#modules/ltimodule/) needs to be enabled. Furthermore LTI users need to be allowed to access Opencast Studio, for this they need the additional role ´ROLE_STUDIO´. The options are:

* **Show the link to opencast studio:** This option renders a button to opencast studio in the block content and the block overview. Opencast studio has to run on your opencast admin node and the following LTI settings have to be configured as well. Defaults to no.
* **Consumer key:** LTI Consumer key for the opencast studio integration.
* **Consumer secret:** LTI Consumer secret for the opencast studio integration.

**Recommendation:** It is possible to configure Opencast Studio to add certain ACLs to the recorded videos. It is recommended to add the same ACLs to recorded videos as to uploaded videos via the block.

## Control episode visibility
In this section you can configure if the teacher is allowed to control the visibility of an Opencast episode after the episode has been processed. The options are:

* **Allow episode visibility control after processing:** If enabled, teachers can control the visibility of an Opencast episode after the episode has been processed in Opencast. Defaults to yes.
* **Allow episode group restriction:** If enabled, teachers can not only control the visibility of an Opencast episode for all course users but can also restrict the visibility to particular course groups. Defaults to yes.

## Add Opencast LTI modules to courses

### Series

In this section you can enable a feature to let teachers add an Opencast [LTI](https://docs.opencast.org/develop/admin/#modules/ltimodule/) series module to the course. This requires that LTI is configured in Opencast. This LTI series module will be pointing to the course's Opencast series.
To be able to use this feature, you have to create a preconfigured LTI tool for showing Opencast series first.

For the preconfigured LTI tool the following settings need to be set:

* **Tool name:** The name of the preconfigured LTI tool. For example: Opencast Series
* **Tool URL:** The URL of the Opencast presentation server followed by `/lti`. For example: `https://develop.opencast.org/lti`
* **Consumer key:** The LTI consumer key.
* **Shared secret:** The LTI shared secret.
* **Custom parameters:** `tool=ltitools/series/index.html`

In the plugin the settings options are:

* **Enable ”Add LTI series module":** If enabled, teachers can add an Opencast LTI series module to a course. This LTI series module will be pointing to the course's Opencast series. The default is no.
* **Default LTI series module title:** The default title to be used when a new Opencast LTI series module is added to a course.
* **Preconfigured LTI tool for series modules:** The preconfigured LTI tool to be used when a new Opencast LTI series module is added to a course.
* **Add series module intro:** If enabled, teachers can add an intro to the Opencast LTI series module. This intro will be shown on the course overview page.
* **Choose series module section:** If enabled, teachers can choose the section which the Opencast LTI series module will be added to.
* **Set series module availability:** If enabled, teachers can set the availability conditions when a new Opencast LTI series module is added to a course. Please note: This feature is only available if availability is globally enabled on the Advanced features admin setting page.

### Episode

You can also enable a feature to let teachers add Opencast [LTI](https://docs.opencast.org/develop/admin/#modules/ltimodule/) episode modules to the course. This requires that LTI is configured in Opencast. These LTI episode modules will be pointing to an Opencast episode.
To be able to use this feature, you have to create a preconfigured LTI tool for showing Opencast episodes first.

For the preconfigured LTI tool the following settings need to be set:

* **Tool name:** The name of the preconfigured LTI tool. For example: Opencast Episodes
* **Tool URL:** The URL of the Opencast presentation server followed by `/lti`. For example: `https://develop.opencast.org/lti`
* **Consumer key:** The LTI consumer key.
* **Shared secret:** The LTI shared secret.
* **Custom parameters:** `tool=paella/ui/watch.html` or `tool=theodul/ui/core.html`

In the plugin the settings options are:

* **Enable ”Add LTI episode module":** If enabled, teachers can add an Opencast LTI episode module to a course. This LTI episode module will be pointing to an Opencast episode. The default is no.
* **Preconfigured LTI tool for episode modules:** The preconfigured LTI tool to be used when a new Opencast LTI episode module is added to a course.
* **Add episode module intro:** If enabled, teachers can add a intro to the Opencast LTI episode module. This intro will be shown on the course overview page.
* **Choose episode module section:** If enabled, teachers can choose the section which the Opencast LTI episode module will be added to.
* **Set episode module availability:** If enabled, teachers can set the availability conditions when a new Opencast LTI episode module is added to a course. Please note: This feature is only available if availability is globally enabled on the Advanced features admin setting page.
