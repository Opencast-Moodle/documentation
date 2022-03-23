# Opencast activity plugin

This activity can be used to display and view Opencast episodes and series in Moodle.
Users with respective privileges (in the following called teacher) can select an existing Opencast episode/series and add it to their course. An embedded player allows students to watch the videos directly in Moodle. As with every activity, the teachers can restrict the access to the videos for students based on e.g. dates, grades or user profiles.
The <a href="https://github.com/polimediaupv/paella">Paella player</a> is used to play the videos.

The <a href="https://moodle.org/plugins/block_opencast">Opencast Videos</a> block also offers the functionality to add activities so that activities can be created faster.

## Installation

The Opencast activity plugin is available from [GitHub](https://github.com/Opencast-Moodle/moodle-mod_opencast) as well as from the [Moodle plugins directory](https://moodle.org/plugins/mod_opencast).

## Requirements

- [tool_opencast](https://github.com/Opencast-Moodle/moodle-tool_opencast)
- Recommended: [block_opencast](https://github.com/Opencast-Moodle/moodle-block_opencast)

## Usage scenarios

In the following, the two usage scenarios, providing a series or an episode, are described.

### Use case 1 - Provide a series ###
The teacher wants to provide a series for students. For example, this series contains all lecture recordings.

Steps to add the activity:
1. Add a new "Video (Opencast)" activity.
2. Enter the Opencast id of the series you want to display:</br>
   <img src="https://user-images.githubusercontent.com/28386141/115534096-b5df3e00-a297-11eb-86c4-f69da06b0038.PNG" width="500"></br>
3. If you want, you can specify further configurations like access restrictions.
4. The videos in the series can be either displayed in a list view or in a preview view:</br>
   <img src="https://user-images.githubusercontent.com/28386141/115258489-523b0080-a131-11eb-9ac1-0819c9aee5a4.png" width="250">
   <img src="https://user-images.githubusercontent.com/28386141/115258708-857d8f80-a131-11eb-81a4-4bdbc295f45e.png" width="250">


### Use case 2 - Provide an episode ###
The teacher wants to provide a single episode for students. For example, this episode belongs to a specific lecture.
1. Add a new "Video (Opencast)" activity.
2. Enter the Opencast id of the episode you want to display as in the previous use case. The activity automatically recognizes that the entered id is an episode.
3. If you want, you can specify further configurations like access restrictions.
4. The activity directly displays a player that shows the video:</br>
   <img src="https://user-images.githubusercontent.com/28386141/115257347-4b5fbe00-a130-11eb-92b6-b3bd2f832972.png" width="500"></br>

   
## Configuration

The configuration of the block is documented in the [settings](settings.md) page.