# Apt

This role is **NO LONGER SUPPORTED**, please take a look to [debops.apt][debops doc apt], [debops.apt_install][debops doc apt_install], [debops.apt_preferences][debops doc apt_preferences] and all others [DebOps apt_* roles][debops doc apt roles].

1. [Overview](#overview)
2. [Role Variables](#role-variables)
3. [Example Playbook](#example-playbook)
4. [Configuration](#configuration)
    * [APT Configuration](#apt-configuration)
    * [Sources List](#sources-list)
    * [Preferences](#preferences)
    * [Tools](#tools)
5. [Development](#development)
6. [License](#license)
7. [Author Information](#author-information)

## Overview

Manage APT repos, preferences and configuration for IPR's servers.

## Role Variables

* **apt_conf_update_pkg_lists** : Period of automatic repositories update in days [default : `1`].
* **apt_conf_download_upgradeable_pkg** : Period of automatic download of upgradeable packages in days [default : `1`].
* **apt_conf_auto_clean_interval** : Period of automatic clean of no longer available packages [default : `0`].
* **apt_conf_purge_list** : The list of default APT configuration files sets by differents packages.
* **apt_conf_purge_manage** : If the purge of default configuration should be managed [default : `true`].
* **apt_src_list_manage** : If apt sources list files should be managed [default : `true`].
* **apt_purge_src_list_file** : If the default sources.file must be absent [default : `true`].
* **apt_stretch_manage** : If Stretch configuration should be managed [default : `true`].
* **apt_default_pref_path** : Path to set the default preferences file for all repositories [default : `/etc/apt/preferences.d/default.pref`].
* **apt_default_pref_tpl** : Template used to generate the previous config file [default : `etc/apt/preferences.d/default.pref.j2`].
* **apt_tools_list** : The list of additionnals tools to install [default [see below](#tools)].
* **apt_tools_state** : State of new tools [default : `installed`].
* **apt_tools_manage** : If those tools should be managed by the role [default : `true`].
* **apt_unwanted_pkg_list** : The list of totally useless packages for a production server [default [see below](#tools)].
* **apt_unwanted_pkg_state** : State of old packages [default : `absent`].
* **apt_unwanted_pkg_manage** : If those old packages should be managed by the role [default : `true`].
* **apt_unattended_upgrades** : If `unattended-upgrades` should be managed by the role [default : `yes`].
* **apt_unattended_upgrades_blacklist** : List of packages to not update (regexp are supported) [default : `[]`].

## Example Playbook

* Use defaults vars :

``` yml
- hosts: serverXYZ
  roles:
    - role: ipr-cnrs.apt
```

* For a system with an X session, you may let the old packages unmanaged :

``` yml
- hosts: serverXYZ
  roles:
    - role: ipr-cnrs.apt
      apt_unwanted_pkg_manage: false
```

## Configuration

### APT Configuration
* Ensure to never remove some packages pattern.
* Set general APT configurations.
* Set periodic actions.
* Set dpkg default values.
* Set unattended-upgrades config.
* Purge default configuration files sets by others apps.

### Sources List
Manage Debian's sources.list :
* Add Stretch repositories (main, security and backports).
* Remove the default `/etc/apt/sources.list` file.
* Update Apt if any repositories modifications.

### Preferences
* Set the preferences for all repositories, default to :
  - Stretch - 510.
  - Stretch Backports - 500.

### Tools
- Ensure to install :
  * aptitude (better than `apt` to resolve dependencies issues)
- Ensure to remove really useless packages from a default installation :
  * laptop-detect (if a server is a laptop…)
  * tasksel (simple interface)
- Manage `unattended-upgrades`.

## Development

This source code comes from our [Gogs instance][apt source] and the [Github repo][apt github] exist just to be able to send the role to Ansible Galaxy…

But feel free to send issue/PR here :)

Thanks to this [hook][gogs to github hook], Github automatically got updates from our [Gogs instance][apt source] :)

## License

[WTFPL][wtfpl website]

## Author Information

Jérémy Gardais
* Source : [on IPR's Gogs][apt source]
* [IPR][ipr website] (Institut de Physique de Rennes)

[gogs to github hook]: https://stackoverflow.com/a/21998477
[apt source]: https://git.ipr.univ-rennes1.fr/cellinfo/ansible.apt
[apt github]: https://github.com/ipr-cnrs/apt
[wtfpl website]: http://www.wtfpl.net/about/
[ipr website]: https://ipr.univ-rennes1.fr/
[debops doc apt_install]: https://docs.debops.org/en/master/ansible/roles/debops.apt_install/index.html
[debops doc apt]: https://docs.debops.org/en/master/ansible/roles/debops.apt/index.html
[debops doc apt_preferences]: https://docs.debops.org/en/master/ansible/roles/debops.apt_preferences/index.html
[debops doc apt roles]: https://docs.debops.org/en/master/search.html?q=debops.apt_&check_keywords=yes
