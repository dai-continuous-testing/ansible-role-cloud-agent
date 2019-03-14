Experitest - Cloud Agent ansible role for mac os hosts
=========

This role will install \ uninstall cloud agent for mac os hosts

Requirements
------------

This role assumes that you have java 8 installed on the instance
Supports mac os hosts only.

Role Variables
--------------

Role variables are as following:
  - app_version: set application version
  - installation_folder: set alternative installation location
  - custom_download_url: works with "download_from_s3: False". provides alternative url to download the zip file
  - state: present \ absent
  - server_port: port number for the process listen to

Example Playbook
----------------

#### [see working example](/example)

In requirements.yml file

    - src: git+https://github.com/ExperitestOfficial/ansible-role-cloud-agent-osx.git
      version: master
      name: cloud-agent-osx


In site.yml file

    - hosts: cloud-agents
      roles:
        - role: cloud-agent-osx
          state: present
          app_version: 12.3.866

To invoke, run the following commands:

- install dependencies \
  *ansible-galaxy install -r requirements.yml*

- run the playbook \
  *ansible-playbook site.yml*
