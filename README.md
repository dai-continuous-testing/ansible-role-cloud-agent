Experitest - Cloud Agent ansible role
=========

This role will install \ uninstall cloud agent for mac os hosts

Requirements
------------

This role assumes that you have java 8 installed on the instance
Supports mac os hosts only.

Role Variables
--------------

| Name | Description | Type | Default | Required |
|------|-------------|:----:|:-----:|:-----:|
| state | should the application be present or absent | present, absent | present | no |
| app_version | application version to install | string | 12.4.5373 | no |
| server_port | port number for the server | number | 8081 | no |
| installation_folder | the folder in which the applction will be installed | string | for mac: ~/experitest/cloud-agent-version <br> for windows: C:\\Experitest\\cloud-agent  | no |
| jmx_port | port number for jmx inspection | number | 51235 | no |
| custom_download_url | custom url to download the installation from (zip format) | string |  | no |
| start_after_install | should application start after installation is completed | boolean | True | no |
| clear_temp_folder | remove temp folder after installation | boolean | False | no |
| clear_before_install | removing old installation before installing new version | boolean | False | no |

Example Playbook
----------------

#### [see working example](/example)

In requirements.yml file

    - src: git+https://github.com/ExperitestOfficial/ansible-role-cloud-agent.git
      version: master
      name: cloud-agent


In site.yml file

    - hosts: cloud-agents
      roles:
        - role: cloud-agent
          state: present
          app_version: 12.3.866

To invoke, run the following commands:

- install dependencies \
  *ansible-galaxy install -r requirements.yml*

- run the playbook \
  *ansible-playbook site.yml*
