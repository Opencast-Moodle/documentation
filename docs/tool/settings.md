# Settings
The plugins allow you, to connect your Moodle instance to multiple Opencast instances. For each instance, you must configure the settings, described below.
The configured instances are listed in the table under *Opencast Instances*. You can add new instances
by clicking on the *Add instance* button.

Next to an automatically set and constant ID, each instance has a name, which you can choose.
The admin settings page of the plugin has an own configuration section for each instance,
that is classified with the name of the corresponding instance. Note, that that section
for a newly added instance will be visible only after saving changes. The same applies to
the deletion of an instance.

Furthermore, each instance has additional options, that can be configured with the table:
* **Is visible to teachers:** If checked, the videos of the corresponding instance are visible in the overview of the block *Opencast Videos* in a course.
Otherwise, the videos of the corresponding instance are hidden.
* **Default:** There must be exactly one default instance. Such an instance has the following additional properties:<br>
  * It is automatically selected in the configuration form of the *Opencast activity plugin*;
  * It is automatically selected in the upload form for a video of the *Opencast activity plugin*;
  * It specifies the allowed video file extensions for an upload of a video file via drag and drop in the activity sections of a course (with edit mode turned on);
  <!--
  * It is used for some pages, if no instance is specified within the corresponding URL;
  * It is used as a default value for *seriesmapping (extends \core\persistent)* via closure;
  -->

Before being able to configure the Opencast API tool, a user has to be created in Opencast. 
That user will be used, to connect to Opencast from within Moodle. It needs to have the following roles in Opencast:

* `ROLE_API`
* `ROLE_API_*`
* `ROLE_SUDO`

Once such a user is created, you must add it to the group `Opencast Project External Applications` *(role `ROLE_GROUP_MH_DEFAULT_ORG_EXTERNAL_APPLICATIONS`)*,
which is created by Opencast by default, or you must add the required external API roles to that user in a different way.
Note, that the roles above are the minimal required roles and additional roles may be added, if required.

The tool plugin has the following configuration options:

* **Opencast API URL:** This is the base URL of the Opencast system. If you have a multiple server setup, this should be the URL of the admin server. Provide the URL including `http://` or `https://`.<br>For example: `https://stable.opencast.org`
* **Username for API calls:** Provide the username of the previously created Opencast user.
* **Password for API user:** Provide the password of the previously created Opencast user.
* **Overall API request execution timeout:**: Configure the time in milliseconds, each API request to Opencast might take until timeout.
* **Connection timeout:** Setup the time in milliseconds, while Moodle is trying to connect to Opencast until timeout.

You can test, whether your API user configuration is correct, by clicking on the *Connection Test Tool* button. 
It shows, whether the tool is able, to reach the Opencast server, and whether it is able to successfully authenticate with the configured API user.

If you want to use LTI, to authenticate users, e.g., for Opencast Studio, you must set the following settings:
* **Consumer key:** LTI Consumer key as configured in Opencast
* **Consumer secret:** LTI Consumer secret as configured in Opencast

LTI must be configured in Opencast, see [LTI](https://docs.opencast.org/develop/admin/#modules/ltimodule/). If you want LTI users to be allowed, to access Opencast studio, you must grant them the additional role `ROLE_STUDIO` in the Opencast LTI configuration.