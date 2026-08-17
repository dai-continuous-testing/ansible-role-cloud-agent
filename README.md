Experitest - Cloud Agent ansible role
=========

This role will install \ uninstall cloud agent for mac os hosts

Requirements
------------

* [ansible-role-java8](https://github.com/ExperitestOfficial/ansible-role-java8) must be installed on all machines. <br>
* Supports mac os hosts only.

Role Variables
--------------

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| state | should the application be present or absent | present, absent | present | no |
| app_version | application version to install | string | 12.12.7794 | no |
| server_port | port number for the server | number | 8081 | no |
| extra_application_properties | additional props to be override in application.properties file | dict | {} | no |
| extra_xml_conf | extand xml configuration | dict | {} | no |
| extra_grid_logback_properties | additional props to be override in grid-logback.properties file | dict | {} | no |
| extra_logback_properties | additional props to be override in logback.properties file | dict | {} | no |
| extra_java_options | extand java options | array of strings | [] | no |
| installer_checksum | sha256 hash value to download and check the integrity of the installer file, to get hash value refer release notes | string |  | no |
| installation_root_folder | the root folder in which the application will be installed under cloud-agent-{version} folder | string | for mac: /Applications/Experitest <br> for windows: C:\\Experitest | no |
| java_version | java jre version to install | string | 8u292-b10 | no |
| custom_download_url | custom url to download the installation from (zip format) | string |  | no |
| custom_download_username | username to download from custom url on windows | string |  | no |
| custom_download_password | password to download from custom url on windows | string |  | no |
| start_after_install | should application start after installation is completed | boolean | True | no |
| clear_temp_folder | remove temp folder after installation | boolean | False | no |
| clear_before_install | removing old installation before installing new version | boolean | False | no |
| kill_notepad | kill notepad/notepadd++ apps on windows | boolean | False | no |
| maintain_supervision_files | maintain supervision files between installations | boolean | False | no |
| download | only download the release version | boolean | True | no || deploy | only deploy the release version | boolean | True | no |
| carplay_service_enabled | deploy the CarPlay XCUITest service (macOS only, opt-in) | boolean | False | no |
| carplay_version | CarPlay service version to install | string | tracks `app_version` | no |
| carplay_custom_download_url | url to download the CarPlay service zip; leave empty to use the S3/CDN default | string |  | no |
| carplay_service_port | port the CarPlay XCUITest service listens on | number | 9726 | no |
| carplay_java_bin | java binary used to run the CarPlay service | string | the agent's JRE (`java_bin`) | no |

CarPlay XCUITest service
------------------------

The role can also deploy the **CarPlay XCUITest service** (macOS only). It is **opt-in and disabled by default** — set `carplay_service_enabled: true` to install it. When enabled, the role installs the service after the agent is deployed and runs it as a per-user `LaunchAgent` on port `9726`, using the agent's JRE.

The download source is chosen automatically from `carplay_custom_download_url`:

* **empty (default)** → download from the S3/CDN release location. Use this in production.
* **set** → download from the given url (e.g. a TeamCity build resolved via `link_finder`). Use this in dev.

**Enable with the S3/CDN release (prod):**

```yaml
- role: cloud-agent
  carplay_service_enabled: true
```

**Enable with a custom/TeamCity build (dev):**

```yaml
- role: cloud-agent
  carplay_service_enabled: true
  carplay_custom_download_url: "{{ carplay_lf.download_url }}"
  carplay_version: "{{ carplay_lf.app_version }}"
```

To remove it, run the role with `state: absent` and `carplay_service_enabled: true`.

Example Playbook
----------------

#### [see working example](/example)
