# General settings

In the following, we outline the settings for the block.
Through the settings, the block can be adjusted to the needs of your platform.
Most of the features the block provides, can be further specified or completely turned off.

The core functionality is to upload a video file to moodle, which is then transferred to opencast.
This is done via a cronjob, which processes all Upload Jobs in a first in first out fashion.

Please make sure that the *Maximum Time limit* for cron execution in *Site administration*->*Server*->*Performance* is not restricted (value of 0 means no timelimit).
Then the cron job is not terminated early.

## Settings for upload jobs

In this section you can define the following settings:

* **Limit upload job by cron:** How many videos are uploaded within one run of the cronjob. If it is set to 0, the number of videos is not limited.
* **Workflow to start after upload:**
  * **Workflow:** Set the unique shortname of the workflow that should be started after successfully uploading a video file to Opencast. When using the default workflows it is recommended to use the `Studio Upload` workflow.
  * **Publish to Engage:**  Select whether the videos should be published to the engage player. This results in the configuration field 'publishToEngage' to be set to `true` or `false` for the called workflow (only useful if the selected workflow supports this). When using the default workflows this checkbox needs to be ticked.
  * Select if multiple videos with the same content hash are uploaded to opencast only once. *This is a legacy feature: Not recommended to be used. With our further development we strive to create one series per course.*
  * Allow unassign from course others a 'delete' icon to the teacher, which will unassign the event from the series of the course. *This is a legacy feature: Only useful if events should not actually be deleted!*
* **Workflow to start before event is be deleted:** Setup the unique shortname of the workflow that should be started for deleting a video file in Opencast. If a workflow is selected, a 'delete' icon is offered to the teacher, which will actually delete the event in the Opencast system. When using the default workflows it is recommended to use the `Delete` workflow. We recommend to use only one of the two previous 'delete' options!
* **Delete videofile from moodle:** This setting causes the Moodle system to delete the file of the uploaded video as soon as possible. If set to false, the video file will remain in the Moodle system in the draft area until a cron job deletes it (usually some days later).
* **Allowed file extensions:** With 'Allowed file extensions' you can specify which file extensions users can upload as videos. The extensions must exist as file types in Moodle under Site administration -> Server -> File types. If left blank all of Moodle's file types in the type group 'video' are allowed.

## Settings for a block instance

In this section the number of videos that is displayed can be configured.

* **Number of videos:** Maximum number of videos to display in the block.
* **Cache valid time:** Time in seconds, before the cache for the video data of each course is refreshed.

## Settings for backup and restore

In this section the backup and restore workflow can be configured. However, the default Opencast workflows do not support this feature. To be able to use this feature two additional workflows need to be added to Opencast. One workflow to duplicate an event in Opencast and another workflow to publish this duplicate. With the default Opencast workflows the [example workflows](backup_restore_workflows.md) can be used.

* **Workflow for duplicating events:** This workflow is needed for restoring opencast events from one course into another. If not set, it is not possible to restore Opencast events. A block instance might be restore, but without a series and without events. In this dropdown menu only workflows with the `api` tag can be selected.

## Group and series

In this section it can be configured how groups and series created by Moodle are named in Opencast. In both cases the options `[COURSEID]` and `[COURSENAME]` are available which are placeholders for the numeric course ID and for the course name. The configuration options are:

* **Create a group:** If checked, a group is created during the upload. This is a legacy feature, which assigns each uploaded event to a Opencast group.
* **Group name:** Group to which the video is added. Important: The group name length is restricted to 128 Bytes. You can use the placeholders [COURSEID] and [COURSENAME] which are automatically replaced.
* **Series name:** Series to which the video is added. You can use the placeholders [COURSEID] and [COURSENAME] which are automatically replaced.

## Roles

In this section you can define which ACL rules are added to a video. You can add and delete roles and define the respective actions for these roles.

This might only be relevant if you want to control the access privileges for your opencast videos via moodle. In this case it is recommended that you setup the moodle-role-provider for your Opencast system (https://docs.opencast.org/develop/admin/configuration/security.user.moodle/).

It is possible to select if roles should be **permanent** or not. Non-permanent roles can be used to manually change the access of certain user groups (e.g. students) for each video.
Roles which are not permanent will be removed if the video is hidden in the block overview and added again if the video is made visible.

To use this feature, you need to define at least one non-permanent role-action combination and the name of opencast workflow for republishing metadata. When using the default Opencast workflows this is `Republish Metadata`. In the video overview of the block, the instructors are able to change the visibility of each video. **However, the icon to do so, is only present if the two requirements mentioned above are met!** This process takes some time, since the opencast workflow needs to finish.

In the ACL Roles the following placeholders can be used:
 * [COURSEID]: Will be replaced by the id of the course.
 * [COURSEGROUPID]: Should only be used in non-permanent roles.
 Dependent on the visibility of the event, it is either replaced by the id of the course or
 (in case the visibility is restricted by groups) it is replaced by a 'G' followed by the id of the group.
 In case that multiple groups are selected in the visibility dialog, one ACL rule for every group is created.
 The basic role including the course id is removed in the case of group visibility.

To give an example for Roles, which also meets the LTI standard and which is used by the plugin by default, you can use the following setting:

| Role                                            | Actions    | Permanent |
| ------------------------------------------------|------------|-----------|
| ROLE_ADMIN                                      | write,read | Yes       |
| ROLE_GROUP_MH_DEFAULT_ORG_EXTERNAL_APPLICATIONS | write,read | Yes       |
| [COURSEID]_Instructor                           | write,read | Yes       |
| [COURSEGROUPID]_Learner                         | read       | No        |

## Metadata

In this section it can be configured which metadata instructors can provide as well as which metadata instructors have to provide. By default instructors have to provide the title of a video.
