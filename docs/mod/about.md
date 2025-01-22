# Opencast activity plugin

The **Opencast Activity** plugin enables the seamless integration of Opencast episodes and series into Moodle courses, providing an efficient way to display and view videos directly within the learning environment.

Users with appropriate permissions (referred to as teachers) can easily select existing Opencast episodes or series and embed them within their courses. The built-in [Paella player](https://github.com/polimediaupv/paella) allows students to watch the videos directly in Moodle without the need for external applications. As with any Moodle activity, teachers can manage access to videos based on criteria such as dates, grades, or user profiles.

In addition to displaying videos, the plugin allows teachers to upload new videos directly to Opencast by simply dragging and dropping video files onto the course homepage while in editing mode.

For added convenience, the [Opencast Videos](https://moodle.org/plugins/block_opencast) block provides an option to quickly create Opencast Activity instances, making it easier and more efficient to integrate videos into Moodle courses.

## Installation

The Opencast Activity plugin can be obtained from the following sources:

- The [GitHub repository](https://github.com/Opencast-Moodle/moodle-mod_opencast), which provides the latest releases, source code, Roadmap and current developments.

- The [Moodle plugins directory](https://moodle.org/plugins/mod_opencast), offering a convenient "Official" installation package directly within Moodle.


## Requirements

The following plugins are required or recommended for the proper functioning of the Opencast Activity plugin:

- **Required:** [Opencast API plugin (tool_opencast)](https://github.com/Opencast-Moodle/moodle-tool_opencast) – Provides core API functionalities for communication with the Opencast system.
- **Recommended:** [Opencast Videos block (block_opencast)](https://github.com/Opencast-Moodle/moodle-block_opencast) – Enhances the user experience by offering additional video management and quick activity creation features.


## Use Case Scenarios

The following use cases describe how the Opencast Activity plugin can be used to provide Opencast series or episodes within Moodle.

### Use Case 1 - Providing a Series

Teachers can provide an entire Opencast series, such as a collection of lecture recordings, to students.

1. Add a new "Video (Opencast)" activity.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/add_activity.png" width="500">

2. Choose the series or manually enter the Opencast series ID to display it.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/configure_activity.png" width="500">

3. Configure additional settings such as access restrictions if needed.

4. The series can be displayed in either a list view or a preview view:

4.1. List View:

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/series_list_view.png" width="500">

4.2. Preview View:

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/series_preview_view.png" width="500">


### Use Case 2 - Providing an Episode

Teachers can provide a single Opencast episode, such as a specific lecture video, to students.

1. Add a new "Video (Opencast)" activity.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/add_activity.png" width="500">


2. Choose the series or manually enter the Opencast episode ID. The system will automatically recognize it as an episode.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/configure_activity_single.png" width="500">

3. Configure additional settings such as access restrictions if needed.

4. The episode will be displayed with an embedded player for immediate viewing.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/video_view.png" width="500">

### Use Case 3 - Uploading a Video via Drag and Drop

Teachers can conveniently upload videos to Opencast by dragging and dropping files onto the Moodle course page (sections).

1. Drag and drop a video file onto a course section while in editing mode.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/dnd.png" width="500">

2. Select "*Upload video file to Opencast*" in the activity/resource dialog and click "Upload".

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/dialog.png" width="500">


3. Locate the newly added Opencast activity in the course section. The name will follow the pattern: "Upload video: [video filename]". Click the activity link.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/new_activity.png" width="500">

4. Fill in the required details and click "Add video".

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/upload_page.png" width="500">

5. A confirmation message will appear on the course page after successful upload.

<img src="https://raw.githubusercontent.com/Opencast-Moodle/documentation/main/docs/img/mod/upload_confirm.png" width="500">

## Configuration

For detailed configuration instructions, refer to the [settings page](settings.md).
