# Shared Settings

This section describes the shared settings available in the Opencast Videos block plugin.

- **Cache valid time:**
  Specifies the duration (in seconds) before the cached video data for each course is refreshed.

  The *Opencast Videos block plugin* utilizes caching to accelerate the display of video data in the embedded block overview in a course.

  It is important to note that the cache for a course is automatically invalidated when the fullscreen overview page of the block is accessed within that course.

- **Moodle to Opencast upload timeout:**
  Defines the maximum duration (in seconds) that a single video upload process is allowed to run during the background uploading task.

  Adjust this setting based on network conditions and server capacity to ensure successful uploads without interruptions.

- **Limit failed upload attempts:**
  Sets a maximum number of failed upload attempts before the upload process is removed from the upload queue.

  When an upload exceeds the specified failure limit, it is moved to an *"Archiving"* state, where upload data is retained but requires manual intervention by teachers or managers to reinitiate the upload process.
