# gklab-ansible
Ansible configuration and playbooks for my gklab home server systems

## gkserver
### initialize gkserver fresh install
`ansible-playbook plays/init_gkserver.yaml --ask-become-pass`

This runs the following tasks:
* `config_essential` - Adds SSH public key, hardens SSH config, sets passwordless sudo for user, creates needrestart file for auto restart after update
* `core_packages` - Performs apt update/upgrade, installs key packages, sets default shell to Fish
* `install_docker` - Installs docker, docker compose, and dependencies
* `install_rclone` - Installs rclone, does not configure
* `install_syncthing` - Install syncthing, does not configure
* `gkserver_repo` - Clones [gkserver repo](https://github.com/rycolos/gkserver-config/tree/main) for scripts and docker compose
* `config_git` - Sets git user, email, and editor
* `config_storage` - Creates backup mount points
* `backup_cronjobs` - Creates backup-related cronjobs, defaulted off. 

### remote apt, docker updates
`ansible-playbook plays/update_sys__apt_docker.yaml --ask-become-pass`

This runs the following tasks:
* `update_apt` - Performs apt update and full upgrade, with autoclean and autoremove
* `update_docker` - Performs pull of docker containers
* `update_reboot` - Reboots machine if necessary