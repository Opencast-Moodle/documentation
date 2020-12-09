# Settings

Before being able to configure the Opencast API tool a user has to be created in Opencast. This user will be used to connect to Opencast from within Moodle. This user needs to have the following roles in Opencast:

* ROLE_API
* ROLE_API_*
* ROLE_SUDO

Once the user is created you can add it to the group `Opencast Project External Applications`.

The tool plugin has the following configuration options:

* **Opencast API URL:** This is the base URL of the Opencast system. If you have a multiple server setup this should be the URL of the admin server. Provide the URL including `https://`. For example: `https://stable.opencast.org`
* **Username for API calls:** Provide the username of the previously created user.
* **Password for API user:** Provide the password of the previously created user.
* **Connection timeout:** Setup the time in seconds while Moodle is trying to connect to opencast until timeout. This defaults to 1 second.
