# Opencast block plugin
This block can be used, to link Moodle courses to Opencast series. 
Users with respective privileges (in the following called instructors) can use this block, to upload videos via Moodle to Opencast. 
These videos are transmitted to the Opencast system by a cronjob and create an event in the respective series there.
Other plugins, like the *Opencast activity plugin*, can be used afterwards, to provide a complete series or a bulk of videos within a course.

The block can be used, to automatically set the access privileges of Moodle users enrolled in the course. 
All events belonging to the series are displayed in the block. 
This way, the instructors get an overview of all recorded lectures as well as planned ones. 
Further, if set up correctly, the instructors are able to restrict the visibility to Moodle groups or prevent access by students at all.

## Installation
The Opencast block plugin is available from [GitHub](https://github.com/Opencast-Moodle/moodle-block_opencast/releases) as well as from the [Moodle plugins directory](https://moodle.org/plugins/block_opencast).

## Requirements
* Installed and configured [Opencast API tool](https://github.com/Opencast-Moodle/moodle-tool_opencast)

## Features
* Upload videos to Opencast
* Record videos using Opencast studio
* Overview of recorded and planned videos in the course
* Overview of all series and videos that a use has access to (independent of a course) ([Global overview](global_overview.md))
* Attaching transcription files to videos
* Send process notifications about videos
* Live status updates of the uploading status and workflow processing states of videos
* Download processed videos from Opencast  
* Edit the video in the Opencast editor
* Edit metadata and delete videos
* Restrict the visibility of videos to Moodle groups or prevent access by students at all
* Allow teachers, to start Opencast workflows for videos
* Linking an existing Opencast series to the course
* Import videos from other Moodle courses via course reuse, series import or manual video bulk import
* Report problems to a support team with automatically including technical information
* In integration with the activity [Opencast Video Provider](https://moodle.org/plugins/mod_opencast):
    + Provide the series or single videos as activity for students to watch directly in Moodle
    + Restrict the visibility using the extensive Moodle activity access settings

## Configuration
The block has many settings, that allow the administrator, to further specify the features or to turn them off.
The configuration of the block is split up into six sections:

* [Shared settings](shared_settings.md)
* [General settings](general_settings.md)
* [Appearance](appearance.md)
* [Additional features](additional_features.md)
* [LTI module features](lti_module_features.md)
* [Import videos features](import_module_features.md)

## Capabilities
There are additional capabilities, with which you can control the access to the features of the block.
Those capabilities are given in an alphabetical order by the following table:

| Capability                           | Role in default configuration             | Description                                                                                                                                                                                                                                                                                                                                                                            |
|--------------------------------------|-------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| block/opencast:addactivity           | editingteacher, manager                   | Add Opencast Video Provider activity for a series to course                                                                                                                                                                                                                                                                                                                            |
| block/opencast:addactivityepisode    | editingteacher, manager                   | Add Opencast Video Provider activity for an episode to course                                                                                                                                                                                                                                                                                                                          |
| block/opencast:addinstance           | editingteacher, manager                   | Add a block instance to a course.                                                                                                                                                                                                                                                                                                                                                      |
| block/opencast:addlti                | editingteacher, manager                   | Add Opencast LTI series module to course                                                                                                                                                                                                                                                                                                                                               |
| block/opencast:addltiepisode         | editingteacher, manager                   | Add Opencast LTI episode module to course                                                                                                                                                                                                                                                                                                                                              |
| block/opencast:addvideo              | editingteacher, manager                   | Add a video via Moodle to opencast                                                                                                                                                                                                                                                                                                                                                     |
| block/opencast:autocompleteteacherroles | editingteacher, teacher                   | One's fullname is used for fullname suggestions in a course for different forms                                                                                                                                                                                                                                                                                                        |
| block/opencast:canchangeownerforallvideos | manager                                   | Can change the owner of videos without being the owner itself                                                                                                                                                                                                                                                                                                                          |
| block/opencast:createseriesforcourse | manager                                   | Create a new series if block/course is not yet associated with one                                                                                                                                                                                                                                                                                                                     |
| block/opencast:defineseriesforcourse | manager                                   | Change the series ID which is associated with the block instance or rather course                                                                                                                                                                                                                                                                                                      |
| block/opencast:deleteevent           | editingteacher, manager                   | Allows to delete a video as specified above                                                                                                                                                                                                                                                                                                                                            |
| block/opencast:directaccessvideolink           | student, teacher, editingteacher, manager | This capability is mainly for those, who received a shared direct access link from a Lecturer and would like to access that video.                                                                                                                                                                                                                                                     |
| block/opencast:downloadvideo         | editingteacher, manager                   | Download processed videos                                                                                                                                                                                                                                                                                                                                                              |
| block/opencast:importseriesintocourse | manager                                   | Can import a series into a course                                                                                                                                                                                                                                                                                                                                                      |
| block/opencast:manageseriesforcourse | manager                                   | Can set the default series of a course and delete series from a course                                                                                                                                                                                                                                                                                                                 |
| block/opencast:manualimporttarget    | editingteacher, manager                   | Manually import videos from other courses                                                                                                                                                                                                                                                                                                                                              |
| block/opencast:manualimportsource    | editingteacher, manager                   | Manually import videos from a course                                                                                                                                                                                                                                                                                                                                                   |
| block/opencast:myaddinstance         | user                                      | Add a block instance to the dashboard.                                                                                                                                                                                                                                                                                                                                                 |
| block/opencast:sharedirectaccessvideolink         | editingteacher, manager      | This is the capability, to give to Lecturers mainly, who would like to share the direct access link to an event with students or anyone else. The feature of sharing a direct access link must be activated in the admin settings and then, Lecturers who have this capability, will have another item in the action menu of each event, which gives them a local Moodle url to share. |
| block/opencast:startworkflow         | editingteacher, manager                   | Start a preconfigured workflow for a video                                                                                                                                                                                                                                                                                                                                             |
| block/opencast:unassignevent         | -                                         | Allows to unassign a video from the series of the course as specified above.                                                                                                                                                                                                                                                                                                           |
| block/opencast:viewunpublishedvideos | editingteacher, manager                   | View the list of all videos of the course, which are available in opencast (even not published ones)                                                                                                                                                                                                                                                                                   |
| block/opencast:viewusers             | manager                                   | View all Moodle users when trying to change the owner of a video on the global overview page                                                                                                                                                                                                                                                                                           |

## Logging
The execution of upload jobs are being logged, which can be viewed at *Site administration*->*Reports*->*Logs*.
View the setting "Site Errors" instead of "All activities" you can view only those upload jobs, which failed.    

## Placement
This plugin is designed as block and, to be used, it will be initially added to a Moodle course by a teacher. The block shows a quick overview over the videos, which are uploaded in the block, but mainly links to a fullscreen overview page, where the full functionality of the plugin is provided.

If you want to provide the plugin in every course by default without requiring, that the teachers adds it to the course, please have a look at Moodle core's `$CFG->defaultblocks` setting which is set in *config.php* only and which is described on https://github.com/moodle/moodle/blob/master/config-dist.php.

As an alternative to placing the block by default, you might also want to add a link to the plugin's overview page to the Boost nav drawer. This plugin does not offer support for adding a Boost nav drawer item itself, but we would like to reference the https://moodle.org/plugins/local_boostnavigation plugin for this job.
After installing *local_boostnavigation* to your Moodle instance, please add the following line to the `local_boostnavigation | insertcustomcoursenodesusers` setting:
```
Opencast Videos|/blocks/opencast/index.php?courseid={courseid}|||editingteacher,manager|admin|OR|fa-film|opencast|grades
```
Please take extra care, that the `editingteacher,manager` list of roles should match the list of roles, who are given the `block/opencast:addvideo` capability in your Moodle instance.
After adding the Boost nav drawer item, you can also remove the `block/opencast:addinstance` capability from all roles, as adding the block is not really necessary anymore.

## Export and import settings
If you want to export and import the administrator settings of the block, you can use the [Admin presets](https://moodle.org/plugins/block_admin_presets) block.
The admin presets block can be added to the frontpage (https://yourmoodlesite.com/?redirect=0). After adding the block, you can select which settings to export or choose a file from which settings should be imported.
In Moodle 4, this functionality is partly integrated into the core.