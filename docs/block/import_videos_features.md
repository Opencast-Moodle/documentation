# Import Videos Features
In this section the backup and restore workflow can be configured. 
However, the default Opencast workflows do not support this feature. 
To be able to use this feature two additional workflows need to be added to Opencast. 
One workflow to duplicate an event in Opencast and another workflow to publish this duplicate. 
With the default Opencast workflows the [example workflows](backup_restore_workflows.md) can be used.

* **Workflow for duplicating events:** This workflow is needed for restoring opencast events from one course into another. 
  If not set, it is not possible to restore Opencast events. 
  A block instance might be restore, but without a series and without events. 
  In this dropdown menu only workflows with the `api` tag can be selected.

If a valid duplication workflow is selected, the following configurations are available:

* **Allow video import within moodle core course import wizard:** If enabled, teachers can import existing video files from other Moodle courses to their Moodle course by using the Moodle core course import wizard. Within the wizard, there is an additional option shown to import the videos which have been uploaded within the Opencast block in the other course. Using this feature, the teacher can import all videos from another course as bulk, but he cannot select individual videos.
  The videos are duplicated in Opencast by an ad-hoc task in Moodle and will show up in the course's video list with a short delay.
* **Allow manual video import:** If enabled, teachers can import existing video files from other Moodle courses to their Moodle course by using a dedicated Opencast video import wizard. This feature is offered on the Opencast block overview page. Using this feature, the teacher can import all or a subset of videos from another course as bulk.
  The videos which are selected within the import wizard are duplicated in Opencast by an ad-hoc task in Moodle and will show up in the course's video list with a short delay.
* **Handle Opencast LTI series modules during manual video import:** If enabled, teachers can handle Opencast series modules which were created with the "Add LTI series module" feature and which relate to the videos which are imported. This especially cleans up modules which have been imported from one course to another course but which still link to the course series of the old course. The series module is instantly handled after the import wizard is finished.
* **Handle Opencast LTI episode modules during manual video import:** If enabled, teachers can handle Opencast episode modules which were created with the "Add LTI episode module" feature and which relate to the videos which are imported. This especially cleans up modules which have been imported from one course to another course but which still link to videos in the old course. The episode modules are handled by an ad-hoc task in Moodle and will be fixed in the course with a short delay.