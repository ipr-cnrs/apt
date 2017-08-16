# Apt

1. [Overview](#overview)
2. [Role Variables](#role-variables)
3. [Example Playbook](#example-playbook)
4. [Configuration](#configuration)
5. [Development](#development)
6. [License](#license)
7. [Author Information](#author-information)

## Overview

Manage APT repos, preferences and configuration for IPR's servers.

## Role Variables

* **apt_src_list_manage** : If apt sources list files should be managed [default : `true`].
* **apt_stretch_manage** : If Stretch configuration should be managed [default : `true`].

## Example Playbook

* Use defaults vars :

``` yml
- hosts: serverXYZ
  roles:
    - role: ipr-cnrs.apt
```

## Configuration

### Sources List

Manage Debian's sources.list :
* Add Stretch repositories.

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
