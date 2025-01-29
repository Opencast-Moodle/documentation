# Development Guide

If you're interested in contributing to the Moodle Opencast plugins, this guide provides essential information to help you understand the development environment and processes.


## Source Control Repositories

All Moodle Opencast plugins are hosted on GitHub under the [Opencast Moodle Plugins organization](https://github.com/Opencast-Moodle).


## Development Lifecycle

Understanding the development lifecycle of Moodle Opencast plugins is crucial for efficient collaboration.
The process typically follows these stages:

### **Issue Creation/Selection:**

* Development begins with an issue in the relevant GitHub repository of the targeted plugin.

* If you're working on an issue (e.g., bug fix or feature request), ensure a **detailed description** is provided before starting development. If the description is unclear, ask the issue creator for clarification.

* Always use the appropriate issue template (e.g., bug report, feature request).

* Assign the issue to yourself to improve tracking and management.

* For discussions or questions, use GitHub Discussions, the Element Community Chat, or contact the repository manager.


### **Development Phase:**

Once an issue is assigned, follow best practices to ensure maintainability and compatibility with other plugins. Key considerations include:


* **Opencast API Class Usage:**

The Opencast PHP Library is integrated into the `tool_opencast` plugin. Use the `opencastapi` property of the `api` class for API calls instead of direct cURL functions, which are deprecated. Example usage:


``` php


use tool_opencast\local\api;
use tool_opencast\exception\opencast_api_response_exception; // Exception handling class

...

$api = api::get_instance($ocinstanceid);
$response = $api->opencastapi->eventsApi->getAll(...);
$code = $response['code'];

if ($code != 200) {
  throw new opencast_api_response_exception($response);
}

...


```

**Note:** More details on the Opencast API Library can be found [here](https://github.com/elan-ev/opencast-php-library/wiki).


* **Unified Exception Handling:**
From `tool_opencast` version **4.5-r4**, the `opencast_api_response_exception` class is introduced to handle API call exceptions in a centralized way. Therefore, using it is highly encouraged!


* **Plugin Interconnectivity:**
Changes in one plugin may impact others. Before making changes, understand how plugins interact, especially the `api` class in `tool_opencast`, which is widely used across all plugins.


* **Coding Standards:**
All plugins follow Moodle's coding standards, enforced through `moodle-plugin-ci` in GitHub Actions.
Always create a pull request instead of directly pushing changes in order to make sure the checks are passed.
A PR is only reviewed if all automated checks pass.


* **Automated Testing:**
If your changes affect existing functionality or introduce new features, include appropriate **PHPUnit** or **Behat** tests to ensure stability.


### **Creating Pull Requests:**

Every change must be submitted via a pull request (PR) against the `main` branch of the targeted plugin.


* Add relevant **labels** to PRs and issues.

* Assign a reviewer **only when all CI checks pass**.

* Ensure PR descriptions are comprehensive, covering dependencies, test scenarios, and additional context.

* Address reviewer feedback promptly to facilitate merging.


### **Developer Group Meetings Participation:**

The Moodle Opencast community holds a **developer group meeting** every second Friday of the month, alternating with core meetings. Participation is encouraged to stay informed about the latest developments, roadmaps, and to ask questions.

For details, check the [official community calendar](https://calendar.google.com/calendar/embed?src=opencast.org_tje2fm34ernnbm0f9saiogp8g0%40group.calendar.google.com&ctz=Europe%2FAmsterdam) and look for **[Moodle] Dev Group Meeting**.
