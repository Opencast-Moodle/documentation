# Settings

In the settings of the repository plugin the repository instances can configured.

## General settings

* **Allow users to add a repository instance into the course**
* **Allow users to add a repository instance into the user context**

## Repositories instances of the site

Note that the repository is only available within a text editor and will paste the URL to the resource into the content. This URL will later be replaced via a Moodle filter to show an embedded player. There are two different possibilities:

* **Display a video using the Moodle media filter:**

    The repository can embed a link to the media file of the Opencast event. This link will automatically be replaced by the Moodle media filter. Be aware that by default Opencast does not protect links to published files in any way. Thus, this link can be easily shared between students, who might not have access to the course itself.
* **Display a video using an Opencast player:**

    The repository can paste a link to the course content, which leads to a page at which an embeddable Opencast player is provided. For this scenario, you will need the [Opencast filter](../filter/about.md) plugin as well as an Opencast instance with [configured LTI](https://docs.opencast.org/develop/admin/modules/ltimodule/). The filter will replace the link by an iFrame, which displays the Opencast player. In order for this to work, the selected publication channel of the repository instance has to serve the URL to the player within the publication URL. Additionally, the filter will automatically authenticate the user in Opencast using LTI. This way, some kind of resource protection is provided.
    However, for increased protection, you would need to activate [stream security](https://docs.opencast.org/develop/admin/configuration/stream-security/) in Opencast.

In this section you see a table of the configured repository instances. You can add instances as well as configure and delete instances.

The possible options per repository instance are:

* **Name:** Name of the repository instance.
* **Opencast default author**
* **Opencast channelid**: The channel id of the publication in Opencast. With a default Opencast installation you can use `engage-player`.
* **Preferred flavor to get thumbnail**: The flavor for the thumbnail. Leave empty for the Opencast default.
* **Fallback flavor to get thumbnail**
* **Embedd URL to player instead of media file.** Whether the URL to the Opencast player should be embedded. If this box is not checked a direct link to a video file will be embedded.
* **Flavor to get video:** The flavor of the video. Leave empty to use the Opencast default.

### Publication channels

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
