# gklab-ansible
Ansible configuration and playbooks for my gklab home server systems

## gkserver
### initialize gkserver fresh install
`ansible-playbook plays/init_gkserver.yaml --ask-become-pass`

### remote apt, docker updates
`ansible-playbook plays/updates.yaml --ask-become-pass`