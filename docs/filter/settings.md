# Settings

The plugin provides the following configuration options:

![Filter opencast configuration](../img/filter_config.png)


1. **URL templates for filtering:** Defines the URL patterns that will be replaced with the Opencast player.

<ul>
   <li>To determine the correct URL, check which URL is inserted into the text by the repository.</li>
   <li>Typically, only one URL needs to be defined.</li>
   <li>
      <p markdown="1">
      Use the placeholder <code>\[EPISODEID]</code> in the URL to indicate where the episode ID should be inserted, e.g., <code>http://stable.opencast.de/play/[EPISODEID]`</code>.
      </p>
   </li>
</ul>

2. **URL to Paella `config.json`:** Specifies an absolute or relative URL to the `config.json` file used by the Paella Player.

<ul>
   <li>
      This configuration file can be customized to modify the appearance or behavior of the Paella Player.
   </li>
</ul>

3. **Enable LTI authentication:** Enables authentication to ensure videos are displayed correctly when Opencast is behind the *Secure Static Files* security layer.

<ul>
   <li>
      When enabled, videos will be displayed in the default Opencast video player.
   </li>
   <li>
      It uses the LTI Credentials configured in Opencast API (tool_opencast) plugin.
   </li>
   <li>
      <p markdown="1">
      <strong>Important Note</strong>: As mentioned in the <em>Opencast API (tool_opencast)</em> plugin [settings](../tool/settings.md), if you plan to use the LTI Authentication feature and have a multi-node Opencast instance, you must add an additional role (<code>ROLE_UI_EVENTS_EMBEDDING_CODE_VIEW</code>) to the Opencast API user's roles to ensure proper functionality.
      </p>
   </li>
</ul>

!!! note

    After configuring this plugin, you must activate it in the filters.
