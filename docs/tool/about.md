# Opencast API plugin

The Opencast API plugin serves as the core integration layer between Moodle and Opencast, providing essential API functions and general settings required by other Opencast-related plugins. This plugin plays a crucial role in managing the relationship between Moodle courses and Opencast series UIDs, ensuring seamless data mapping and synchronization.

In addition to storing course-to-series associations, the Opencast API plugin offers web service endpoints that facilitate interaction with external tools such as the [Opencast role provider](https://docs.opencast.org/develop/admin/#configuration/security.user.moodle/), enabling streamlined user role management.

Furthermore, the plugin acts as the central hub for communication and configuration, offering core functionalities, shared utilities, and foundational classes that support the operation of other Opencast plugins within Moodle. By utilizing this plugin, institutions can efficiently manage Opencast integrations, ensuring consistent and scalable workflows across their learning environments.

## Installation

The Opencast API plugin can be obtained from the following sources:

- The [GitHub repository](https://github.com/Opencast-Moodle/moodle-tool_opencast/releases), which provides the latest releases, source code, Roadmap and current developments.

- The [Moodle plugins directory](https://moodle.org/plugins/tool_opencast), offering a convenient "Official" installation package directly within Moodle.

## Configuration

For detailed configuration instructions, refer to the [settings page](settings.md).

**NOTE**: Starting from 2025, major settings of the Opencast Videos plugin will be integrated into the Opencast API plugin.
