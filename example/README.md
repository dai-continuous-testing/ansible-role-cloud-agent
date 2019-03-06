
# Example usage

to use the example:
- cd into the example folder

- install dependencies \
  *ansible-galaxy install -r requirements.yml*

- run the playbook \
  *ansible-playbook site.yml -i inventory.ini -k --ask-sudo-pass*

- put the admin password and confirm

## Known issues

- mac os - it might throw the error "boto3 is not installed" \
  make sure pip is configured in path \
  to fix - add the line *export PATH="/usr/local/bin:$PATH"* to ~/.bashrc file

