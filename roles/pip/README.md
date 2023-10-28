Ansible Role Template
=========

[![Molecule test](https://github.com/diademiemi/ansible_collection_diademiemi.python/actions/workflows/ansible-role-pip.yml/badge.svg)](https://github.com/diademiemi/ansible_collection_diademiemi.python/actions/workflows/ansible-role-pip.yml)

This is an Ansible role to install Python pip and install packages.

It can also place the annoying `break-system-packages = true` in `~/.config/pip/pip.conf` to allow users to install packages.

Requirements
------------
These platforms are supported:
- Ubuntu 20.04
- Ubuntu 22.04
- Debian 10
- Debian 11
- EL 8 (Tested on Rocky Linux 8)
- EL 9 (Tested on Rocky Linux 9)
- Fedora 38
- openSUSE Leap 15.4

<!--
- List hardware requirements here  
-->

Role Variables
--------------

Variable | Default | Description
--- | --- | ---
`python_pip_allow_user_install_packages` | `[]]` | Users that have the configuration to install packages that may be incompatible with the system
`python_pip_config_dir` | `"~/.config/pip"` | Directory to place `{{ python_pip_config_file }}`
`python_pip_config_file` | `"{{ python_pip_config_dir }}/pip.conf"` | File to place `break-system-packages = true`
`python_pip_global_packages` | `[]` | List of packages to install globally. Args: `name`, `version`
`python_pip_user_packages` | `[]` | List of packages to install for every user. Args: `user`, `packages`
<!--
`variable` | `default` | Variable example
`long_variable` | See [defaults/main.yml](./defaults/main.yml) | Variable referring to defaults
`distro_specific_variable` | See [vars/debian.yml](./vars/debian.yml) | Variable referring to distro-specific variables
-->

Dependencies
------------
<!-- List dependencies on other roles or criteria -->
None

Example Playbook
----------------

```yaml
- name: Use diademiemi.pip role
  hosts: "{{ target | default('pip') }}"
  roles:
    - role: "diademiemi.pip"
      tags: ['diademiemi', 'pip', 'setup']    ```

```

License
-------

MIT

Author Information
------------------

- diademiemi (@diademiemi)

Role Testing
------------

This repository comes with Molecule tests for Docker on the supported platforms.
Install Molecule by running

```bash
pip3 install -r requirements.txt
```

Run the tests with

```bash
molecule test
```

These tests are automatically ran by GitHub Actions on push. If the tests are successful, the role is automatically published to Ansible Galaxy.

