# LTI Module Features
In this section, you can enable a feature, to let teachers add an Opencast [LTI](https://docs.opencast.org/develop/admin/#modules/ltimodule/) module to the course. This requires, that LTI is configured in Opencast.

## Add Opencast LTI series modules to courses
These settings are specific to the LTI module for Opencast series. This LTI series module will be pointing to the course's Opencast series.
To be able to use this feature, you have to create a preconfigured LTI tool, for showing Opencast series first.

For the preconfigured LTI tool the following settings need to be set:

* **Tool name:** The name of the preconfigured LTI tool. For example: Opencast Series
* **Tool URL:** The URL of the Opencast presentation server followed by `/lti`. For example: `https://develop.opencast.org/lti`
* **Consumer key:** The LTI consumer key.
* **Shared secret:** The LTI shared secret.
* **Custom parameters:** `tool=ltitools/series/index.html`

In the plugin the settings options are:

* **Enable ”Add LTI series module":** If enabled, teachers can add an Opencast LTI series module to a course. This LTI series module will be pointing to the course's Opencast series. Defaults to no.
* **Default LTI series module title:** The default title to be used, when a new Opencast LTI series module is added to a course. Default to *Opencast videos*.
* **Preconfigured LTI tool for series modules:** The preconfigured LTI tool to be used, when a new Opencast LTI series module is added to a course.
* **Add series module intro:** If enabled, teachers can add an intro to the Opencast LTI series module. This intro will be shown on the course overview page. Defaults to no.
* **Choose series module section:** If enabled, teachers can choose the section, to which the Opencast LTI series module will be added to. Defaults to no.
* **Set series module availability:** If enabled, teachers can set the availability conditions, when a new Opencast LTI series module is added to a course. Please note: This feature is only available, if availability is globally enabled on the *Advanced features* admin setting page. Defaults to no.

## Add Opencast LTI episode modules to courses
These settings are specific to the LTI module for Opencast episodes. These LTI episode modules will be pointing to an Opencast episode.
To be able, to use this feature, you have to create a preconfigured LTI tool, for showing Opencast episodes first.

For the preconfigured LTI tool the following settings need to be set:

* **Tool name:** The name of the preconfigured LTI tool. For example: Opencast Episodes
* **Tool URL:** The URL of the Opencast presentation server followed by `/lti`. For example: `https://develop.opencast.org/lti`
* **Consumer key:** The LTI consumer key.
* **Shared secret:** The LTI shared secret.
* **Custom parameters:** `tool=paella/ui/watch.html` or `tool=theodul/ui/core.html`

In the plugin the settings options are:

* **Enable ”Add LTI episode module":** If enabled, teachers can add an Opencast LTI episode module to a course. This LTI episode module will be pointing to an Opencast episode. Defaults to no.
* **Preconfigured LTI tool for episode modules:** The preconfigured LTI tool to be used when a new Opencast LTI episode module is added to a course.
* **Add episode module intro:** If enabled, teachers can add an intro to the Opencast LTI episode module. This intro will be shown on the course overview page. Defaults to no.
* **Choose episode module section:** If enabled, teachers can choose the section, which the Opencast LTI episode module will be added to. Defaults to no.
* **Set episode module availability:** If enabled, teachers can set the availability conditions, when a new Opencast LTI episode module is added to a course. Please note: This feature is only available if availability is globally enabled on the *Advanced features* admin setting page. Defaults to no.
