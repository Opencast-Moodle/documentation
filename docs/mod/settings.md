# Settings

## General settings

The Opencast Activity plugin includes three mandatory settings that can be configured by the administrator.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/settings_part_1.png" width="500">


1. **Opencast Channel:** Specifies the Opencast channel where videos are published. Only videos published in this channel can be displayed within the activity. The publication must include media files, such as `.mp4` files, that are compatible with the Paella player.


2. **URL to Paella config.json:** Defines the path to the Paella player configuration file. Administrators can modify this configuration to customize the player's appearance and behavior.


3. **URL to Paella theme.json:** Specifies the path to the Paella player theme file. This can be adjusted to change the player's visual appearance.


## Download settings

The Opencast Activity plugin offers a download feature that allows students to download videos via a dropdown menu.

To enable this feature, the administrator must configure the **Opencast Download Channel** setting. This setting must reference a valid publication channel that includes downloadable media files, such as `.mp4` files.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/settings_part_2.png" width="500">


By default, the download feature is disabled at the activity level, requiring teachers to enable it manually. However, administrators can enable the **Allow download by default** option to create an "opt-out" scenario, where downloads are enabled by default and teachers must disable them manually if desired.

Additionally, the **Force student download** setting ensures that the download option is always available to students and prevents teachers from modifying download permissions.
