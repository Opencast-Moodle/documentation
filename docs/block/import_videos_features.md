# Import Videos Features
In this section the backup and restore workflow can be configured. 

* **Allow video import:** If enabled, teachers can import existing video files from other Moodle courses to their Moodle course.

There are two modes for importing videos:
* **Duplicating Events:** A new series is created during the import and all events are duplicated. By default, Opencast does not support this feature. Thus two additional workflows need to be configured. One workflow to duplicate an event in Opencast and another workflow to publish this duplicate.
  With the default Opencast workflows the [example workflows](backup_restore_workflows.md) can be used.
* **ACL Change:** The existing series will be connected with the target course so that all events are shared between the courses. This avoids duplicated series but changes are always reflected in both courses.

* **Workflow for duplicating events:** This workflow is needed for importing opencast events from one course into another when the Duplication mode is selected. If not set, it is not possible to import Opencast events.

If a valid duplication workflow is selected, the following configurations are available:

* **Allow video import within moodle core course import wizard:** If enabled, teachers can import existing video files from other Moodle courses to their Moodle course by using the Moodle core course import wizard. Within the wizard, there is an additional option shown to import the videos which have been uploaded within the Opencast block in the other course. Using this feature, the teacher can import all videos from another course as bulk, but he cannot select individual videos.
  The videos are duplicated in Opencast by an ad-hoc task in Moodle and will show up in the course's video list with a short delay.
* **Allow manual video import:** If enabled, teachers can import existing video files from other Moodle courses to their Moodle course by using a dedicated Opencast video import wizard. This feature is offered on the Opencast block overview page. Using this feature, the teacher can import all or a subset of videos from another course as bulk.
  The videos which are selected within the import wizard are duplicated in Opencast by an ad-hoc task in Moodle and will show up in the course's video list with a short delay.
* **Handle Opencast series modules during manual video import:** If enabled, teachers can handle Opencast series modules which were created with the "Add LTI series module" feature and which relate to the videos which are imported. Activities of the type `mod_opencast` are also cleaned up. This especially cleans up modules which have been imported from one course to another course but which still link to the course series of the old course. The series module is instantly handled after the import wizard is finished.
* **Handle Opencast episode modules during manual video import:** If enabled, teachers can handle Opencast episode modules which were created with the "Add LTI episode module" feature and which relate to the videos which are imported. Activities of the type `mod_opencast` are also cleaned up. This especially cleans up modules which have been imported from one course to another course but which still link to videos in the old course. The episode modules are handled by an ad-hoc task in Moodle and will be fixed in the course with a short delay.