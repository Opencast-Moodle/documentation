# Opencast block plugin

This block can be used to link moodle courses to Opencast series. 
Users with respective privileges (in the following called instructors) can use this block to upload videos via moodle to Opencast. 
These videos are transmitted to the Opencast system by a cronjob and create an event in the respective series there.

The block can be used to automatically set the access privileges of moodle users enrolled in the course. 
All events belonging to the series are displayed in the block. 
This way, the instructors get an overview of all recorded lectures as well as planned ones. 
Further, if setup correctly, the instructors are able to restrict the visibility to moodle groups or prevent access by students at all.

## Installation

The Opencast block plugin is available from [GitHub](https://github.com/Opencast-Moodle/moodle-block_opencast/releases) as well as from the [Moodle plugins directory](https://moodle.org/plugins/block_opencast).

## Requirements
* Installed and configured [Opencast API tool](https://github.com/Opencast-Moodle/moodle-tool_opencast)

## Features
* Upload videos to Opencast
* Record videos using Opencast studio
* Overview of recorded and planned videos in the course
* Overview of all series and videos that a use has access to (independent of a course)
* Download processed videos from Opencast  
* Edit the video in the Opencast editor
* Edit metadata and delete videos
* Restrict the visibility of videos to moodle groups or prevent access by students at all
* Allow teachers to start Opencast workflows for videos
* Linking an existing Opencast series to the course
* Import videos from other moodle courses by duplicating them
* Report problems to a support team with automatically including technical information
* In integration with the activity [Opencast Video Provider](https://moodle.org/plugins/mod_opencast):
    + Provide the series or single videos as activity for students to watch directly in moodle
    + Restrict the visibility using the extensive moodle activity access settings


## Configuration

The block has many settings that allow the administrator to further specify the features or to turn them off.
The configuration of the block is split up into six sections:

* [General settings](general_settings.md)
* [Appearance](appearance.md)
* [Additional features](additional_features.md)
* [LTI module features](lti_module_features.md)
* [Import videos features](import_module_features.md)
* [Workflow settings](workflow_settings.md)

## Capabilities

There are additional capabilities, with which you can control the access to the features of the block.

| Capability                           | Role in default configuration | Description                                                                                          |
|--------------------------------------|-------------------------------|------------------------------------------------------------------------------------------------------|
| block/opencast:addactivity           | editingteacher, manager       | Add Opencast Video Provider activity for a series to course |
| block/opencast:addactivityepisode    | editingteacher, manager       | Add Opencast Video Provider activity for an episode to course |
| block/opencast:addinstance           | editingteacher, manager       | Add a block instance to a course. |
| block/opencast:addlti                | editingteacher, manager       | Add Opencast LTI series module to course |
| block/opencast:addltiepisode         | editingteacher, manager       | Add Opencast LTI episode module to course |
| block/opencast:addvideo              | editingteacher, manager       | Add a video via Moodle to opencast |
| block/opencast:canchangeownerforallvideos | manager                  | Can change the owner of videos without being the owner itself |
| block/opencast:createseriesforcourse | manager                       | Create a new series if block/course is not yet associated with one |
| block/opencast:defineseriesforcourse | manager                       | Change the series ID which is associated with the block instance or rather course |
| block/opencast:deleteevent           | editingteacher, manager       | Allows to delete a video as specified above |
| block/opencast:downloadvideo         | editingteacher, manager       | Download processed videos |
| block/opencast:importseriesintocourse | manager                      | Can import a series into a course |
| block/opencast:manageseriesforcourse | manager                       | Can set the default series of a course and delete series from a course |
| block/opencast:manualimporttarget    | editingteacher, manager       | Manually import videos from other courses |
| block/opencast:manualimportsource    | editingteacher, manager       | Manually import videos from a course |
| block/opencast:myaddinstance         | user                          | Add a block instance to the dashboard. |
| block/opencast:startworkflow         | editingteacher, manager       | Start a preconfigured workflow for a video |
| block/opencast:unassignevent         | -                             | Allows to unassign a video from the series of the course as specified above. |
| block/opencast:viewunpublishedvideos | editingteacher, manager       | View the list of all videos of the course, which are available in opencast (even not published ones) |
| block/opencast:viewusers             | manager                       | View all Moodle users when trying to change the owner of a video on the global overview page |

## Logging

The execution of upload jobs are being logged, which can be viewed at *Site administration*->*Reports*->*Logs*.
View the setting "Site Errors" instead of "All activities" you can view only those upload jobs, which failed.    

## Placement

This plugin is designed as block and, to be used, it will be initially added to a Moodle course by a teacher. The block shows a quick overview over the videos which are uploaded in the block, but mainly links to a fullscreen overview page where the full functionality of the plugin is provided.

If you want to provide the plugin in every course by default without requiring that the teachers adds it to the course, please have a look at Moodle core's $CFG->defaultblocks setting which is set in config.php only and which is described on https://github.com/moodle/moodle/blob/master/config-dist.php.

As an alternative to placing the block by default, you might also want to add a link to the plugin's overview page to the Boost nav drawer. This plugin does not offer support for adding a Boost nav drawer item itself, but we would like to reference the https://moodle.org/plugins/local_boostnavigation plugin for this job.
After installing local_boostnavigation to your Moodle instance, please add the following line to the `local_boostnavigation | insertcustomcoursenodesusers` setting:
```
Opencast Videos|/blocks/opencast/index.php?courseid={courseid}|||editingteacher,manager|admin|OR|fa-film|opencast|grades
```
Please take extra care that the `editingteacher,manager` list of roles should match the list of roles who are given the `block/opencast:addvideo` capability in your Moodle instance.
After adding the Boost nav drawer item, you can also remove the `block/opencast:addinstance` capability from all roles as adding the block is not really necessary anymore.

## Export and import settings
If you want to export and import the administrator settings of the block, you can use the [Admin presets](https://moodle.org/plugins/block_admin_presets) block.
The admin presets block can be added to the frontpage (https://yourmoodlesite.com/?redirect=0). After adding the block, you can select which settings to export or choose a file from which settings should be imported.
In Moodle 4, this functionality is partly integrated into the core.