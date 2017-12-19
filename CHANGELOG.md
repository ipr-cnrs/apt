
## v1.0.x

### Enhancements
* Add Stretch-Security repository.
* Update README.md with example.
* Rename apt_old_* to apt_unwanted_* vars.
* Fix tasks name.
* Add possibility to define APT preferences for Proxmox reposity.

## v1.0.2

### Fix
* Purge sources.list default file after setting up all new repositories…

## v1.0.1

### Fix
* Ensure to update cache before install unattended-upgrades.

## v1.0

### Features
* Remove the default `/etc/apt/sources.list` file.
* Manage Stretch repositories.
* Update Apt if any repositories modifications.
* Manage default preferences file.
* Ensure to install some additionnals tools (aptitude,…).
* Ensure to remove really useless packages (laptop-detect, tasksel,…).
* Ensure to never remove some packages pattern.
* Manage general, periodic and dpkg config files.
* Purge default configuration files sets by others apps.
* Manage `unattended-upgrades` (package and config).
