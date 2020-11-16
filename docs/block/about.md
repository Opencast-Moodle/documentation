# Opencast block plugin

This block can be used to link Moodle courses to Opencast series. Users with respective privileges (in the following called instructors) can use this block to upload videos via Moodle to Opencast. These videos are transmitted to the Opencast system by the cronjob and create an event in the respective series there.

 The block can be used to automatically set the access privileges of moodle users enrolled in the course. All events belonging to the series are displayed in the block. This way, the instructors get an overview of all recorded lectures as well as planned ones. Further, if setup correctly, the instructors are able to restrict the visibility to moodle groups or prevent access by students at all.

## Installation

The Opencast block plugin is available from [GitHub](https://github.com/Opencast-Moodle/moodle-block_opencast/releases) as well as from the [Moodle plugins directory](https://moodle.org/plugins/block_opencast).

## Requirements

* Min. Moodle Version: 3.3
* Opencast API level:
   * Minimum: v1.0.0
   * Recommended: v1.1.0
    * Some features might do not works as expected, when using an older API level.
* Installed Opencast api tool.

## Configuration

The configuration of the block is split up into three sections:

* [General settings](general_settings.md)
* [Appearance](appearance.md)
* [Additional features](additional_features.md)

## Capabilities

There are additional capabilities, with which you can control the access to the features of the block.

| Capability                           | Role in default configuration | Description                                                                                          |
|--------------------------------------|-------------------------------|------------------------------------------------------------------------------------------------------|
| block/opencast:addvideo              | editingteacher, manager       | Add a video via moodle to opencast.                                                                   |
| block/opencast:viewunpublishedvideos | editingteacher, manager       | View the list of all videos of the course, which are available in opencast (even not published ones) |
| block/opencast:defineseriesforcourse | manager       | Change the series ID which is associated with the block instance or rather course |
| block/opencast:createseriesforcourse | manager       | Create a new series if block/course is not yet associated with one |
| block/opencast:deleteevent           | editingteacher, manager       | Allows to delete a video as specified above. |
| block/opencast:unassignevent         | -                              | Allows to unassign a video from the series of the course as specified above. |

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
