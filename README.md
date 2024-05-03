# RPi_ansible
Ansible scripts for setting up my Raspberry Pi labs

## Tips
- When a device needs a sudo/become password, you should execute the ansible playbook with the `--ask-become-pass` parameter:

### Syntax
`ansible-playbook -i hosts/hosts.ini --ask-become-pass system-update.yaml`
