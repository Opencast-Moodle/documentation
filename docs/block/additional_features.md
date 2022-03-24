# Additional Features
In the additional features you can configure the access to Opencast Studio, the visibility of episodes, the activity module settings as well as some other features.

## Settings for the chunkuploader
If you also have the chunkuploader installed, you configure it in this section.

* **Enable Chunkupload:** If Chunkupload is enabled, it will be possible to upload videos using the chunkupload plugin. Defaults to yes.
* **Video size limit:** Limit the file size of uploaded videos through the chunkupload. The default is 2GB.
* **Offer filepicker as alternative:** If this option is enabled, a checkbox labeled as 'Use Moodle default file picker to access all repositories' will be shown below the chunk upload widget. As soon as this checkbox is checked, the chunk upload widget is hidden and the Moodle default file picker is shown, giving access to all Moodle repositories.

## Opencast studio integration
In this section you can enable the feature to add [Opencast Studio](https://docs.opencast.org/develop/admin/#modules/studio/) support to the block. The options are:

* **Show the link to opencast studio:** This option renders a button to opencast studio in the block content and the block overview.
* **Redirect to Studio in a new tab:** When enabled, studio opens in a new tab.
* **Opencast Studio Base URL:** The base URL to be used to call Opencast studio. The base URL of the opencast instance is used if empty.
* **Show a redirect back button in Studio:** When enabled, Studio then renders an additional button "Exit and go back" after up- or downloading the recording.
* **Label for Studio's return button:** This label works as a short description where the return link leads to. This label will be appended to the Studio return button text, when empty, moodle site name will be passed as label.
* **Custom Studio return endpoint URL:** When empty the return url redirects back to the same Moodle opencast block overview where the request comes from. A custom endpoint URL will then be passed to Studio as return url when configured, in this case, admin is able to use 2 placeholders including [OCINSTANCEID] and [COURSEID]. Please NOTE: the URL must be relative to wwwroot.

If LTI is configured in tool_opencast, the access to Opencast studio is initiated with LTI so that users are directly authenticated. 

**Recommendation:** It is possible to configure Opencast Studio to add certain ACLs to the recorded videos. It is recommended to add the same ACLs to recorded videos as to uploaded videos via the block.

## Opencast editor integration
In this section you can enable the feature to add [Opencast Editor](https://github.com/opencast/opencast-editor) support to the block. The options are:

* **Show the link to opencast editor in the action menu:** This option renders a button to opencast editor in the block content and the block overview. The following settings as well lti credentials have to be configured as well.
* **Opencast Editor Base URL:** The base URL to be used to call the Opencast Editor, the base url of the opencast instance is used if empty.
* **Opencast Editor Endpoint:** The editor endpoint to access the editor. The mediapackage ID will be added at the end of the url.

If LTI is configured in tool_opencast, the access to the Opencast editor is initiated with LTI so that users are directly authenticated.

## Engage player integration
If you use this configuration, the video titles in the block overview are displayed as link to the engage player. If LTI is configured in tool_opencast, the user will be authenticated with LTI before redirected to the engage player.

* **URl of the Opencast Engage server**: Absolute URL to the engage server. If empty, the video titles in the overview are not linked to the engage player.

## Notifications
In this section you can configure if teachers should receive notifications about the processing status of videos after upload.

* **Allow event process status notification:** This option allows the system to send notification about the status of the uploaded video from Opencast during the process to the users. This option only includes uploader of the video into the user list. To Notify all teachers of the course, the following setting should be enabled.
  This feature is done through a scheduled task that is recommended to run every minute.
* **Notify all course teachers about the event process status:** With this option, apart from the uploader of the video, all the teachers of the course where the video is uploaded from get notified about the Opencast processing status.
* **Cleanup notification jobs after (Days):** This setting sets a deadline in day for the jobs that are not yet completed. After the deadline has reached, the job will be deleted despite its process state.
  This features helps to remove the pending notification jobs from the list and it is done through a scheduled task that is recommended to run once a day.
  NOTE: (zero) "0" value disables the setting.

## Control episode visibility
In this section you can configure if the teacher is allowed to control the visibility of an Opencast episode after the episode has been processed. The options are:

* **Enable visibility control:** If enabled, teachers can control the visibility of an Opencast episode on upload.
* **Allow episode visibility control after processing:** If enabled, teachers can control the visibility of an Opencast episode after the episode has been processed in Opencast. Defaults to yes.
* **Allow episode group restriction:** If enabled, teachers can not only control the visibility of an Opencast episode for all course users but can also restrict the visibility to particular course groups. Defaults to yes.
* **Waiting time for scheduled visibility change (Minutes):** It defines a minimum waiting time (in minutes) that scheduled visibility change process should wait. This time span will be added to current time for the scheduled video change date filed in add video form, it will also be used to validate that field. Based on how fast the Opencast instance processes the videos, this waiting time could be configured.
  NOTE: When empty or (zero) "0", the default value is used.

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
* **Workflow tag:** Tag for Opencast workflow definitions that can be configured and started by teachers.
* **Support email:** If not empty, teachers can report problems for their uploaded videos. An email with technical information as well as a message entered by the teachers is sent to this support email address.
* **Terms of use:** If not empty, a checkbox with the terms of use will appear on the "Video upload" page. Teachers must accept the entered terms of use before they can upload a video.