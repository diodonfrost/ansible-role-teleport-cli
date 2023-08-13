# ansible-role-teleport-cli

[![molecule](https://github.com/diodonfrost/ansible-role-teleport-cli/workflows/molecule/badge.svg)](https://github.com/diodonfrost/ansible-role-teleport-cli/actions)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-diodonfrost.teleport_cli-660198.svg)](https://galaxy.ansible.com/diodonfrost/teleport_cli)

This role provide a compliance for install teleport_cli on your target host.

## Requirements

This role was developed using Ansible 2.5 Backwards compatibility is not guaranteed.
Use `ansible-galaxy install diodonfrost.teleport_cli` to install the role on your system.
*   Ansible >= 2.8
*   Python >= 2.7

## Role Variables

This role has multiple variables. The defaults for all these variables are the following:

```yaml
---
# defaults file for teleport_cli

# Define teleport version to install (example: 13.3.2)
# Possible values: https://api.github.com/repos/gravitational/teleport/releases
# Default: latest
teleport_version: latest

# Define where to download teleport package url
# Default: use local system path defined in Ansible vars/*.yml
teleport_pkg_url: "{{ default_teleport_pkg_url }}"

# Define where to install teleport binary
# Default: use local system path defined in Ansible vars/*.yml
teleport_bin_directory: "{{ default_teleport_bin_directory }}"

# Define where to download teleport archive
# Default: use tmp system path defined in Ansible vars/*.yml
teleport_tmp_directory: "{{ default_teleport_tmp_directory }}"
```

## Dependencies

None

## Example Playbook

This is a sample playbook file for deploying the Ansible Galaxy teleport_cli role in a localhost and installing the latest version of teleport_cli.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: diodonfrost.teleport_cli
```

This role can also install a specific version of teleport_cli.

```yaml
---
- hosts: localhost
  become: true
  roles:
    - role: ansible-role-teleport_cli
      vars:
        teleport_version: 13.3.2
```

## Local Testing

This project uses [Molecule](http://molecule.readthedocs.io/) to aid in the
development and testing.

To develop or test you'll need to have installed the following:

* Linux (e.g. [Ubuntu](http://www.ubuntu.com/))
* [Docker](https://www.docker.com/)
* [Python](https://www.python.org/) (including python-pip)
* [Ansible](https://www.ansible.com/)
* [Molecule](http://molecule.readthedocs.io/)
* [Libvirt](https://libvirt.org/) (if you test windows system)
* [Vagrant](https://www.vagrantup.com/downloads.html) (if you test windows system)

### Testing with Docker

```shell
# Install requirements
pip install -r requirements-dev.txt

# Test ansible role with ubuntu 22.04
molecule test

# Test ansible role with ubuntu 20.04
image=ansible-ubuntu:20.04 molecule test

# Test ansible role with alpine latest
image=ansible-alpine:latest molecule test

# Create ubuntu 22.04 instance
molecule create

# Apply role on ubuntu 22.04 instance
molecule converge

# Launch tests on ubuntu 22.04 instance
molecule verify
```

### Testing with Vagrant and Libvirt

```shell
# Test ansible role with Windows
molecule test -s windows
```

## License

Apache 2

## Author Information

This role was created in 2019 by diodonfrost.
