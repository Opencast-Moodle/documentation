# Workflow Settings
In this section, you can configure the workflows that can be started by the teachers for single videos.
Only workflows with the correct tag specified in [Additional features](additional_features.md) are available to configure.

You can enable or disable each workflow. Disabled workflows are not displayed and cannot be started by teachers. 

Furthermore, the workflow can be configured using the options provided by the *configuration panels*. 
These configurations are part of the workflow definition and must be configured in Opencast.
The HTML code of the configuration panels is directly served from Opencast which is why it is embedded in an iframe.

Currently, the configuration panels can contain checkboxes, radio buttons and text inputs (including number fields). 
Further input types might also work but are not officially supported or tested at the moment.

If workflows are deleted in Opencast or don't have the configured tag anymore, the option to delete these workflows is available.