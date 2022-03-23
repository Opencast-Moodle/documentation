# Settings
The plugins allow you to connect your Moodle instance to multiple Opencast instances. For each instance, you must configure the following settings.

Before being able to configure the Opencast API tool, a user has to be created in Opencast. 
This user will be used to connect to Opencast from within Moodle. This user needs to have the following roles in Opencast:

* ROLE_API
* ROLE_API_*
* ROLE_SUDO

Once the user is created you can add it to the group `Opencast Project External Applications`.

The tool plugin has the following configuration options:

* **Opencast API URL:** This is the base URL of the Opencast system. If you have a multiple server setup this should be the URL of the admin server. Provide the URL including `https://`. For example: `https://stable.opencast.org`
* **Username for API calls:** Provide the username of the previously created user.
* **Password for API user:** Provide the password of the previously created user.
* **Overall API request execution timeout:**: Configure the time in milliseconds each API request to Opencast might take until timeout.
* **Connection timeout:** Setup the time in milliseconds while Moodle is trying to connect to opencast until timeout.

You can test if your API user configuration is correct by clicking on the *Connection Test Tool* button. 
It shows if the tool is able to reach the Opencast server and if it is able to successfully authenticate with the configure API user.

If you want to use LTI to authenticate users e.g. for Opencast Studio, you must set the following settings:
* **Consumer key:** LTI Consumer key as configured in Opencast
* **Consumer secret:** LTI Consumer secret as configured in Opencast