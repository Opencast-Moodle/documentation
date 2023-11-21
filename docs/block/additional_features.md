# Additional Features
In this section, you can configure the *chunkuploader*, the access to Opencast Studio, the access to Opencast Editor, the visibility of episodes, the activity module settings, the settings for transcriptions as well as some other features.

## Settings for the chunkuploader
If you also have the *chunkuploader* installed, you configure it in this section.

* **Enable Chunkupload:** If enabled, it will be possible, to upload videos using the *chunkupload* plugin. Defaults to yes.
* **Video size limit:** Limits the file size of uploaded videos through the *chunkupload*. The default is 2.0 GB.
* **Offer filepicker as alternative:** If this option is enabled, a checkbox, labeled as 'Use Moodle default file picker to access all repositories' will be shown below the *chunkupload* widget. As soon as this checkbox is checked, the *chunkupload* widget is hidden and the Moodle default file picker is shown, giving access to all Moodle repositories. Defaults to yes.

## Opencast Studio integration
In this section, you can enable the feature, to add [Opencast Studio](https://docs.opencast.org/develop/admin/#modules/studio/) support to the block. The options are:

* **Show the link to opencast studio:** This option renders a button to Opencast Studio in the block content and the block overview. Defaults to no.
* **Redirect to Studio in a new tab:** If enabled, the Opencast Studio opens in a new tab. Defaults to yes.
* **Opencast Studio Base URL:** The base URL, to be used to call Opencast Studio. The base URL of the associated Opencast instance is used, if empty. Defaults to empty.
* **Show a redirect back button in Studio:** When enabled, Opencast Studio then renders an additional button "Exit and go back" after up- or downloading the recording. Defaults to no.
* **Label for Studio's return button:** This label works as a short description, where the return link leads to. This label will be appended to the Opencast Studio return button text. If empty, the Moodle site name will be passed as label. Defaults to empty.
* **Custom Studio return endpoint URL:** If empty, the return URL redirects back to the same Moodle Opencast block overview, where the request comes from. A custom endpoint URL will then be passed to Opencast Studio as return URL, if configured. In this case, an admin is able, to use two placeholders including [OCINSTANCEID] and [COURSEID]. Please NOTE: The URL must be relative to `wwwroot`. Defaults to `/blocks/opencast/index.php?courseid=[COURSEID]&ocinstanceid=[OCINSTANCEID]`.
* **Custom Studio settings filename:** This custom settings filename will be appended to the query, when redirecting to Opencast Studio. Afterwards Opencast Studio looks for that filename relative to its directory and reads its settings from that file. Note, that this feature requires Opencast 14.2 or later. Defaults to empty.

If LTI is configured in the *Opencast API plugin*, the access to Opencast Studio is initiated with LTI, so that users are directly authenticated. 

**Recommendation:** It is possible, to configure Opencast Studio, to add certain ACLs to the recorded videos. It is recommended, to add the same ACLs to recorded videos as to uploaded videos via the block.

## Opencast Editor integration
In this section, you can enable the feature, to add [Opencast Editor](https://github.com/opencast/opencast-editor) support to the block. The options are:

* **Show the link to opencast editor in the action menu:** This option renders a button to Opencast Editor in the block content and the block overview. The other settings of this section and the LTI credentials have to be configured as well. Defaults to no.
* **Opencast Editor Base URL:** The base URL to be used, to call the Opencast Editor. The base URL of the associated Opencast instance is used, if empty. Defaults to empty.
* **Opencast Editor Endpoint:** The Opencast Editor endpoint, to access the editor. The *mediapackage* ID will be added at the end of that URL. Defaults to `/editor-ui/index.html?mediaPackageId=`.

If LTI is configured in the *Opencast API plugin*, the access to the Opencast Editor is initiated with LTI, so that users are directly authenticated.

## Engage player integration
If you use this configuration, the video titles in the block overview are displayed as links to the Engage player. If LTI is configured in the *Opencast API plugin*, the user will be authenticated with LTI before being redirected to the Engage player.

* **URl of the Opencast Engage server**: Absolute URL to the Engage server. If empty, the video titles in the overview are not linked to the Engage player. Defaults to empty.

## Notifications
In this section, you can configure, whether teachers should receive notifications about the processing status of videos after upload.

* **Allow event process status notification:** This option allows the system, to send notifications about the status of uploaded videos from Opencast during the process to the users. This option only includes the uploader of the video in the user list. To notify all teachers of the course, the setting *Notify all course teachers about the event process status* should be enabled.
  This feature is realized through a scheduled task, that is recommended to run every minute. Defaults to no.
* **Notify all course teachers about the event process status:** With this option, apart from the uploader of the video, all the teachers of the course, where the video is uploaded from, get notified about the Opencast processing status (see the setting *Allow event process status notification*). Defaults to no.
* **Cleanup notification jobs after (Days):** This setting sets a deadline in days for the jobs, that are not yet completed. After the deadline was reached, the job will be deleted despite its process state.
  This features helps, to remove the pending notification jobs from the list, and it is done through a scheduled task, that is recommended to run once a day. Defaults to 0.<br>
  NOTE: (zero) "0" value disables the setting.

## Control episode visibility
In this section, you can configure, whether the teacher is allowed, to control the visibility of an Opencast episode, after the episode has been processed. The options are:

* **Enable visibility control:** If enabled, teachers can control the visibility of an Opencast episode on upload. Defaults to yes.
* **Allow episode visibility control after processing:** If enabled, teachers can control the visibility of an Opencast episode after the episode has been processed in Opencast. Defaults to yes.
* **Allow episode group restriction:** If enabled, teachers can not only control the visibility of an Opencast episode for all course users, but can also restrict the visibility to particular course groups. Defaults to yes.
* **Waiting time for scheduled visibility change (Minutes):** It defines a minimum waiting time (in minutes), that a scheduled visibility change process should wait. This time span will be added to the current time for the scheduled video change date field in the add video form. It will also be used, to validate that field. Based on how fast the Opencast instance processes the videos, this waiting time could be configured. Defaults to 20.<br>
  NOTE: When empty or (zero) "0", the default value is used.

## Opencast activity modules
If you also have the *Opencast Video Provider* activity installed, you can configure it in this section.

* **Enable Opencast activity:** If enabled, teachers can add an activity for the series to the course. Defaults to no.
* **Default activity title:** Default title, that is used, when a new Opencast activity is added to a course. Defaults to *Opencast videos*.
* **Add series module intro:** If enabled, teachers can add a description to the Opencast activity series module, that is shown on the course overview page. Defaults to no.
* **Choose series module section:** If enabled, teachers can choose the section, to which the Opencast activity series module will be added to. Defaults to no.
* **Set series module availability:** If enabled, teachers can set the availability conditions, when a new Opencast LTI series module is added to a course. Defaults to no.
* **Enable Opencast activity for episodes:** If enabled, teachers can add activities for episodes to the course. Defaults to no.
* **Add episode module intro:** If enabled, teachers can add a description to the Opencast activity episode module, that is shown on the course overview page. Defaults to no.
* **Choose episode module section:** If enabled, teachers can choose the section, to which the Opencast activity episode module will be added to. Defaults to no.
* **Set episode module availability:** If enabled, teachers can set the availability conditions, when a new Opencast activity episode module is added to a course. Defaults to no.

For the availability features, the *Enable restricted access* feature must be activated in the global settings.

## Settings for Transcription
In this section, you can configure, whether transcription files can be attached to videos and different features
as well as properties for those transcription files.

* **Workflow for transcription (speech to text):** This workflow is triggered, when transcription files are attached to the video. If not set, uploading and managing transcriptions is not provided.
By setting this workflow, a new section to upload transcription files in the add video page as well as a new action menu item in the overview page are provided, to upload/handle the new/current transcriptions files. 
Defaults to empty.
* **Workflow for delete transcription:** This workflow is triggered, when a transcription is deleted. It is required, to provide the deletion feature in order for an event, to be processed correctly.
NOTE: If empty, the feature will be disabled. Defaults to empty.
* **Allow download transcriptions:** If enabled, the transcription download button will be displayed in the manage transcriptions page, by which teachers are able, to download the transcriptions file.
NOTE: In case you are using Opencast 13 or later, you need to make sure, that all prerequisites including LTI features and permissions to access */assets/* endpoint for LTI users, are set correctly, as it is mandatory, to perform LTI call.
Defaults to yes.
* **Transcription Service Types (Flavors):** These service types (flavors) will be presented as select (dropdown) options, to select from, when uploading transcriptions. It is a key-value pair of information, by which the keys are consumed by Opencast and values are human-readable information, that describe the type of transcription service.
**(Multi-Language filters)** In order for each value of the dropdown (select) to get translated using filters such as [Multi-Language Content (v2)](https://moodle.org/plugins/filter_multilang2), each value should contain the placeholder, defined by that filter i.e. *"{mlang en}Amberscript German{mlang}{mlang de}Amberscript Deutsch{mlang}"*.
* **Maximum number of sets to upload:** Specifies, how many transcription boxes should be provided to teachers, to upload. In the case, that it is not correctly set, only one field set will be provided.
Defaults to 3.
* **Allowed transcription file extensions:** Comma separated list of allowed transcription file extensions (extensions must exist in Moodle's *File types* list). If left blank, all extensions with the type *'HTML track files'* are allowed (again see *File types*).

For the transcription features to work properly, the Opencast user should have the following roles:
* `ROLE_UI_EVENTS_DETAILS_ASSETS_EDIT`
* `ROLE_UI_EVENTS_DETAILS_ASSETS_VIEW`
* `ROLE_UI_EVENTS_DETAILS_MEDIA_VIEW`
* `ROLE_GROUP_MH_DEFAULT_ORG_SYSTEM_ADMINS`

For the setting *workflow for transcription* and for the setting *workflow for delete transcription* the following sample Opencast workflow *Republish metadata and captions* may be used:
```
<?xml version="1.0" encoding="UTF-8"?>
<definition xmlns="http://workflow.opencastproject.org">

  <id>republish-metadata-and-captions</id>
  <title>Republish metadata and captions</title>
  <tags>
    <tag>api</tag>
  </tags>

  <operations>

    <!-- Publish to engage player -->

    <operation
      id="publish-engage"
      exception-handler-workflow="partial-error"
      description="Update recording in Opencast Media Module">
      <configurations>
        <configuration key="download-source-flavors">dublincore/*,security/*,captions/*</configuration>
        <configuration key="strategy">merge</configuration>
        <configuration key="check-availability">false</configuration>
      </configurations>
    </operation>

    <!-- Clean up work artifacts -->

    <operation
        id="cleanup"
        fail-on-error="false"
        description="Remove temporary processing artifacts">
      <configurations>
        <configuration key="delete-external">true</configuration>
        <configuration key="preserve-flavors">security/*</configuration>
      </configurations>
    </operation>

  </operations>
</definition>
```

## Live Status Update
In this section, you can configure, whether uploading status and workflow processing states of videos will be watched and are visible.

* **Enable live status update feature:** If enabled, uploading status and workflow processing states will be watched, when they are in an ongoing process.
This is done, by pulling the status information for those processes in a one-second interval. Defaults to yes.
* **Page reload timeout (in seconds):** The timeout in seconds, by which the page will be reloaded, when there is an updated status identified. If empty or less than 0, a default value of 3 seconds will be considered.
NOTE: Before reloading the page, a teachers will be notified. The reload is important, so that every required backend process takes place. Defaults to 3.

## Workflows Privacy Notice
In this section, you can configure the privacy notice for workflows in the start workflow dialog.

* **Workflow Privacy Notice Info Text:** This input is used, to provide information about privacy notice for workflows in the start workflow dialog.
NOTE: If empty, no notice will be displayed. Defaults to empty.
* **Workflows Definition List:** A comma separated list of workflow definitions, by which the privacy notice is displayed. When empty, the privacy notice will be displayed for all workflows. Defaults to empty.
* **Workflow Privacy Notice Title:** A title, to be displayed in start workflow dialog. It is intended, to be configurable in order, to be adjusted by the users. When empty, default string is used. Defaults to empty.

## Additional features
In this section, unrelated configurations are collected.

* **Download channel:** If not empty, teachers can download processed videos. The video files are served from the specified Opencast channel. Defaults to *api*.
* **Direct access channel:** Opencast publication channel, from which the videos are served, when accessing them directly. Leaving this option empty, will disable the feature. Defaults to empty.
NOTE: It is recommended, to take further caution when using this feature, since it reveals the direct video data on the Opencast server upon accessing the link.
* **Workflow tag:** Comma separated list of tags for Opencast workflows, that can be configured by the admin and manually started by teachers. Defaults to empty.
* **Support email:** Email address, to which reports are sent, if users report problems with videos. Defaults to empty.
* **Terms of use:** If you enter some text, a checkbox with the terms of use will appear on the "Video upload" page. The users must accept the entered terms of use, before they can upload the video. Defaults to empty.