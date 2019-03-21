
# Example usage

to use the example:
- cd into the example folder

- install dependencies \
  *ansible-galaxy install -r requirements.yml*

- run the playbook \
  *ansible-playbook site.yml -i inventory.ini -k --ask-sudo-pass*

- put the admin password and confirm

## Known issues

- dependencies like Java8 must be installed before run the playbook

- for windows target:
  - add the command *export OBJC_DISABLE_INITIALIZE_FORK_SAFETY=YES*
  - pip install "pywinrm>=0.2.2"

- windows target:
  run the bootstrap script in the target machine
  NOTE: *update username and password first*



