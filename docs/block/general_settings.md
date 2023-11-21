# General Settings
This section explains the general settings, that affect the core functionality of the block.
The core functionality is to upload a video file to Moodle, which is then transferred to Opencast.
This is done via a cronjob, which processes all Upload Jobs in a first in first out fashion.

Please make sure, that the *Maximum Time limit* for cron execution in *Site administration*->*Server*->*Performance* is not restricted (value of 0 means no time limit).
Then the cron job is not terminated early.

## Settings for upload jobs
In this section you can define the following settings:

* **Limit upload job by cron:** How many videos are uploaded within one run of the cronjob. If it is set to 0, the number of videos is not limited.
* **Workflow to start after upload:** Set the unique shortname of the workflow that should be started after successfully uploading a video file to Opencast. When using the default workflows it is recommended to use the `Studio Upload` workflow.
* **Publish to Engage:**  Select whether the videos should be published to the engage player. This results in the configuration field 'publishToEngage' to be set to `true` or `false` for the called workflow (only useful if the selected workflow supports this). When using the default workflows this checkbox needs to be ticked.
* **Ingest upload:** Use the Opencast ingest service for uploading videos. For this to work, you must have configured ingest nodes in your Opencast instance.
* **Reuse existing uploads:** Select if multiple videos with the same content hash are uploaded to opencast only once. *This is a legacy feature: Not recommended to be used. With our further development we strive to create one series per course.*
* **Allow unassign from course** others a 'delete' icon to the teacher, which will unassign the event from the series of the course. *This is a legacy feature: Only useful if events should not actually be deleted!*
* **Workflow to start before event is be deleted:** Setup the unique shortname of the workflow that should be started for deleting a video file in Opencast. If a workflow is selected, a 'delete' icon is offered to the teacher, which will actually delete the event in the Opencast system. When using the default workflows it is recommended to use the `Delete` workflow. We recommend to use only one of the two previous 'delete' options! With Opencast 10, this option is usually not required anymore since videos are automatically retracted before deletion.
* **Delete videofile from Moodle:** This setting causes the Moodle system to delete the file of the uploaded video as soon as possible. If set to false, the video file will remain in the Moodle system in the draft area until a cron job deletes it (usually some days later).
* **Allowed file extensions:** With 'Allowed file extensions' you can specify which file extensions users can upload as videos. The extensions must exist as file types in Moodle under Site administration -> Server -> File types. If left blank all of Moodle's file types in the type group 'video' are allowed.
* **Maximum number of series:** Specifies how many series can be assigned to a course. Teachers won't be able to add/import more series if the maximum number is reached.

## Settings for a block instance
In this section the number of videos that is displayed can be configured.

* **Number of videos:** Maximum number of videos to display in the block.

## Group and series
In this section it can be configured how groups and series created by Moodle are named in Opencast. In both cases the options `[COURSEID]` and `[COURSENAME]` are available which are placeholders for the numeric course ID and for the course name. The configuration options are:

* **Create a group:** If checked, a group is created during the upload. This is a legacy feature, which assigns each uploaded event to a Opencast group.
* **Group name:** Group to which the video is added. Important: The group name length is restricted to 128 Bytes. You can use the [placeholders](#placeholders) which are automatically replaced.
* **Series name:** Series to which the video is added. You can use the [placeholders](#placeholders) which are automatically replaced.

## Roles
In this section you can define, which ACL roles are added to a video. You can add and delete roles and define the respective actions for those roles.

That might be relevant only, if you want to control the access privileges for your Opencast videos via Moodle. In this case, it is recommended, that you set up the *moodle-role-provider* for your Opencast system (https://docs.opencast.org/develop/admin/configuration/security.user.moodle/).

It is possible, to select, whether roles should be **permanent** or not. Non-permanent roles can be used, to manually change the access of certain user groups (e.g. students) for each video.
Roles, which are not permanent, will be removed, if the video is hidden in the block overview, and added again, if the video is made visible.

To use this feature, you need to define at least one non-permanent role-action combination and the name of Opencast workflow for republishing metadata. Use the setting `Workflow for updating metadata`, to specify that workflow.
When using the default Opencast workflows that is `Republish Metadata`. In the video overview of the block, the instructors are able to change the visibility of each video.
This process takes some time, since the Opencast workflow needs to finish.<br>
**However, the icon to do so, is only present, if the two requirements mentioned above are met!**

In the ACL roles you can use [placeholders](#placeholders).

To give an example for roles, which also meets the LTI standard and which is used by the plugin by default, you can use the following setting:

| Role                                            | Actions    | Permanent |
| ------------------------------------------------|------------|-----------|
| ROLE_ADMIN                                      | write,read | Yes       |
| ROLE_GROUP_MH_DEFAULT_ORG_EXTERNAL_APPLICATIONS | write,read | Yes       |
| [COURSEID]_Instructor                           | write,read | Yes       |
| [COURSEGROUPID]_Learner                         | read       | No        |

You can also specify an owner role, that identifies the owner of a video/series, with the setting `ACL owner role`. The role must also be specified in the roles table. The role must be permanent and include a user-related placeholder, e.g. `ROLE_OWNER_[USER_EMAIL]`. It should not include any course-related placeholders.

## Event Metadata
In this section, it can be configured, which metadata instructors can provide as well as which metadata instructors have to provide, for uploading videos to Opencast. By default, instructors have to provide the title of a video.

## Series Metadata
In this section, it can be configured, which metadata instructors can provide as well as which metadata instructors have to provide, for creating Opencast series. By default, instructors have to provide the title, the rights holder and the license of a series.

## Placeholders
For some settings, you can use placeholders, that are replaced, when dealing with names for Opencast (e.g. when creating a series). 
The following placeholders are available:

* **[COURSEID]**: Will be replaced by the id of the course.
* **[COURSENAME]**: Will be replaced by the name of the course.
* **[COURSEGROUPID]**:  Should only be used in non-permanent roles.
  Depending on the visibility of the event, it is either replaced by the id of the course or
  (in case the visibility is restricted by groups) it is replaced by a 'G' followed by the id of the group.
  In case that multiple groups are selected in the visibility dialog, one ACL rule for every group is created.
  The basic role including the course id is removed in the case of group visibility.
* **[USERNAME]**:: Will be replaced by the name of the user who uploaded a video or created a series. Roles with this placeholder must be permanent.
  - **[USERNAME_LOW]**: Username in lowercase.
  - **[USERNAME_UP]**: Username in uppercase.
  - **[USER_EMAIL]**: Email of the user.
  - **[USER_EXTERNAL_ID]**: External ID of the user.
  