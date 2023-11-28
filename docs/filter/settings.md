# Settings
There are only two settings for the Opencast filter.

![Filter opencast configuration](../img/filter_config.png)

* **URL templates for filtering:** URLs matching this template are replaced with the Opencast player. 
To define the correct URL, you should check which URL is inserted into a text by the repository. In general, you must define only one URL. In the URL, you must use the placeholder *\\[EPISODEID]*, to indicate, where the episode ID is contained in the URL, e.g. `http://stable.opencast.de/play/[EPISODEID]`.
* **URL to Paella config.json:** Defines an absolute or relative URL to the `config.json`, that is used by the Paella Player. This config can be adapted, if you want to modify the look or behavior of the Paella player.

Once you configured the filter, you need to activate the filter.