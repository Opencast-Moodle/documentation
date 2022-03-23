# Settings

In the settings of the repository plugin the repository instances can configured.
The possible options per repository instance are:

* **Name:** Name of the repository instance.
* **Opencast instance:** The Opencast instance from which the repository retrieves videos.
* **Opencast default author:** The default author that is displayed for a video if the creator is not given. Empty by default.
* **Opencast channelid:**: The channel id of the publication in Opencast. With a default Opencast installation you can use `engage-player`.
* **Preferred flavor to get thumbnail:**: The flavor for the thumbnail. Leave empty for the Opencast default.
* **Fallback flavor to get thumbnail:** Fallback flavor for the thumbnail if there is no thumbnail for the preferred flavor.
* **Embedd URL to player instead of media file.** Whether the URL to the Opencast player should be embedded. If this box is not checked, a direct link to a video file will be embedded.
* **Flavor to get video:** The flavor of the video. Leave empty to use the Opencast default.

### Publication channels
Opencast publishes its events in so called publication channels.
One default publication channel is e.g. the `engage-player` channel.
Each publication has a publication URL, which points to the page under which the video is published (e.g. an HTTP page with the Opencast player).
Additionally, publications can contain a set of media data with URLs to the media files themselves (e.g. an MP4 file).

For the configuration of the publication channel you can either use the default publication channel `engage-player` or use your own publication channel. To use your own publication channel you will have to modify the publish workflow and add a `publish-configure` operation. For example:

```
<operation
  id="publish-configure"
  exception-handler-workflow="partial-error"
  description="Publish to external api publication channel">
  <configurations>
    <configuration key="channel-id">api</configuration>
    <configuration key="mimetype">application/json</configuration>
    <configuration key="source-tags">engage-download,engage-streaming</configuration>
    <configuration key="url-pattern">https://HOSTNAME/paella/ui/watch.html?id=${event_id}</configuration>
    <configuration key="with-published-elements">false</configuration>
    <configuration key="check-availability">true</configuration>
  </configurations>
</operation>

```