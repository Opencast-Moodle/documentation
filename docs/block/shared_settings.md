# Shared Settings
This section explains the shared settings.

* **Cache valid time:** Time in seconds, before the cache for the video data of each course is refreshed.<br>
The *Opencast block plugin* uses that cache, to provide the video data, that is shown by the embedded block overview in a course, faster.
Note, that that cache is invalidated for a course, if the fullscreen overview page of the block is loaded for that course.
* **Moodle to Opencast upload timeout:** Configures the time in seconds, a single video upload may take during the background uploading task.