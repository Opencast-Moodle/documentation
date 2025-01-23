# Settings

The configuration settings for the Opencast Chunkupload plugin are divided into two parts: general plugin settings and auxiliary settings within the Opencast Videos block (`block_opencast`) plugin.

## General settings:

The Opencast Chunkupload plugin provides several configurable options for administrators.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/chunkupload/settings.png" width="500">

1. **Chunk size (MB):** Defines the size (in MB) of each video file chunk to be uploaded.

2. **Duration until unused token is deleted:** Specifies the time period after which unused upload tokens will be deleted automatically.

3. **Duration until uncompleted file upload is deleted:** Specifies the duration after which incomplete file uploads will be removed.

4. **Duration until completed file upload is deleted:** Sets the retention period for successfully uploaded files before they are automatically deleted as part of the cleanup process.

---

## Auxiliary Settings in Opencast Videos Block Plugin

When the _Chunkupload_ plugin is installed, the Opencast Videos block plugin (`block_opencast`) automatically includes a dedicated settings section under the [**Additional features**](../block/additional_features.md) section. This section, titled **"Settings for the chunkuploader"**, allows administrators to control Chunkupload functionality within the block plugin.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/chunkupload/block_settings_1.png" width="500">

1. **Enable Chunkupload:** Enables or disables the ability to upload videos using the chunkupload plugin.

2. **Video file size limitation mode:** Determines whether to enforce a file size limit. If "Limited video size" is selected, the administrator can define the limit in the subsequent setting.

3. **Video size limit:** Specifies the maximum allowed video file size if the limitation mode is enabled.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/chunkupload/block_settings_2.png" width="500">

4. **Offer filepicker as alternative:** If enabled, users can choose to use the regular Moodle file picker instead of the chunkupload functionality via a checkbox.
