# Raspberry Pi Ansible Configs
Ansible configs for setting up and configuring my Raspberry Pi devices.

`system-update.yaml` - runs the apt update and apt upgrade commands as sudo (no reboot after update)

`docker_cleanup.yml` - cleans up dangling docker images

## Ansible Commands and Parameters

### Basic Commands:
- `ansible-playbook playbook.yml`: Execute an Ansible playbook.
- `ansible-playbook playbook.yml --check`: Perform a dry-run to check changes without making them.
- `ansible-playbook playbook.yml --tags <tag_name>`: Run specific tasks in a playbook based on their tags.
- `ansible-playbook playbook.yml --skip-tags <tag_name>`: Skip tasks in a playbook based on their tags.

### Inventory Management:
- `ansible-inventory --list`: Display the current inventory in JSON format.
- `ansible-inventory --graph`: Display the current inventory in graphical form.
- `ansible-inventory -i inventory_file`: Specify an inventory file to use.

### Vault Management:
- `ansible-vault encrypt <file>`: Encrypt a file.
- `ansible-vault decrypt <file>`: Decrypt a file.
- `ansible-vault edit <file>`: Edit an encrypted file.
- `ansible-vault rekey <file>`: Change the encryption password of a file.

### Ad-Hoc Commands:
- `ansible <host_group> -m <module> -a "<arguments>"`: Run an ad-hoc command on a host group.
- `ansible <host> -a "<command>"`: Run an ad-hoc command on a specific host.

### Playbook Structure:
- `hosts`: Define the hosts or host groups to target.
- `tasks`: Define the tasks to be executed.
- `vars`: Define variables to be used within the playbook.
- `roles`: Organize tasks into reusable roles.

### Playbook Parameters:
- `name`: Name of the task or play.
- `hosts`: Specify the hosts or host groups to target.
- `become`: Enable privilege escalation (sudo).
- `vars`: Define variables for the playbook or individual tasks.
- `tags`: Assign tags to tasks for selective execution.
- `when`: Conditionally execute tasks based on defined conditions.
- `ask-vault-pass`: Prompt for the vault password to decrypt encrypted files.
- `ask-become-pass`: Prompt for the privilege escalation (sudo) password.
- `ask-pass`: Prompt for the SSH password when connecting to hosts.
- `ask-sudo-pass`: Prompt for the sudo password (deprecated, use `ask-become-pass`).

### Ansible Tower CLI (Ansible Automation Platform CLI):
- `ansible-cli inventory list`: List inventories.
- `ansible-cli inventory create <name> --description <description>`: Create a new inventory.
- `ansible-cli job_template list`: List job templates.
- `ansible-cli job_template create <name> --inventory <inventory_id>`: Create a new job template.
- `ansible-cli job launch <job_template_id>`: Launch a job based on a job template.

For more information, refer to the [Ansible Documentation](https://docs.ansible.com/).

### Tips
- When a device needs a sudo/become password, you should execute the ansible playbook with the `--ask-become-pass` parameter.
- Search all sections for `CHANGE_ME`. These values need to be changed before execution.

### CLI Command(s)
- `ansible-playbook -i hosts/hosts.ini --ask-become-pass system-update.yaml`

