# Settings

## General settings
The activity has three mandatory settings, that can be modified by the administrator.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/settings_part_1.png" width="500"></br>

The first configuration **Opencast Channel** specifies the Opencast channel, to which the videos are published. Only videos published in this channel can be displayed with this activity. The publication must include media files, e.g. `.mp4` files, that can be served to the paella player.

The second configuration **URL to Paella config.json** specifies the path to the Paella player config. This config can be adapted, if you want to modify the look or behavior of the Paella player.

The third configuration **URL to Paella theme.json** specifies the path to the Paella player theme. This config can be adapted, if you want to modify the look of the Paella player.

## Download settings
In the activity a dropdown menu can be provided, allowing students, to download videos.
To activate this functionality, the setting **Opencast Download Channel** must be configured. It must contain a valid publication channel, that contains media files such as `.mp4` files.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/settings_part_2.png" width="500"></br>

The download functionality is implemented on activity level. By default, it is deactivated and teachers have to activate it explicitly. However, administrators can activate the setting **Allow download by default**, to create an "Opt-out" scenario. In this case, the download is generally enabled and teachers have to disable it explicitly.

The last setting **Force student download** prevents teachers from configuring the download functionality. Students can always download videos.
