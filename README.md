Experitest - Cloud Agent ansible role
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

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: cloud-agents
      roles:
         - { role: experitest.cloud-agent, state: present }

License
-------

BSD

Author Information
------------------

