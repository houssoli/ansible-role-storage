# [storage](#storage)

Create partitions, volume groups, volumes, filesystems and mounts

|Travis|GitHub|Quality|Downloads|Version|
|------|------|-------|---------|-------|
|[![travis](https://travis-ci.com/robertdebock/ansible-role-storage.svg?branch=master)](https://travis-ci.com/robertdebock/ansible-role-storage)|[![github](https://github.com/robertdebock/ansible-role-storage/workflows/Ansible%20Molecule/badge.svg)](https://github.com/robertdebock/ansible-role-storage/actions)|[![quality](https://img.shields.io/ansible/quality/38205)](https://galaxy.ansible.com/robertdebock/storage)|[![downloads](https://img.shields.io/ansible/role/d/38205)](https://galaxy.ansible.com/robertdebock/storage)|[![Version](https://img.shields.io/github/release/robertdebock/ansible-role-storage.svg)](https://github.com/robertdebock/ansible-role-storage/releases/)|

## [Example Playbook](#example-playbook)

This example is taken from `molecule/resources/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: robertdebock.storage
```

The machine may need to be prepared using `molecule/resources/prepare.yml`:
```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes
  serial: 30%

  roles:
    - role: robertdebock.bootstrap
```

For verification `molecule/resources/verify.yml` run after the role has been applied.
```yaml
---
- name: Verify
  hosts: all
  become: yes
  gather_facts: yes

  tasks:
    - name: check if connection still works
      ping:
```

Also see a [full explanation and example](https://robertdebock.nl/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# defaults file for storage

storage_default_fstype: ext4

# storage_partitions:
#   - name: /dev/sdb
#     number: 1
#     part_end: 4GiB
#   - name: /dev/sdb
#     number: 2
#     flags:
#       - lvm
#     part_start: 4GiB
#     part_end: 8GiB

# Sizes in megabytes, minumum of 4.
# storage_volumegroups:
#   - name: group1
#     device: /dev/sdb2
#     size: 128
#   - name: group2
#     device: /dev/sdb2
#     size: 256

# Sizes in megabytes.
# storage_volumes:
#   - name: var1
#     vg: group1
#     size: 16

# storage_filesystems:
#   - name: /dev/group1/var
#     filesystem: ext4

# storage_mounts:
#   - name: /var
#     src: /dev/group1/var1
#     owner: root
#     group: root
#     mode: 755
#     opts: defaults
#     boot: yes
#     dump: 0
#     passno: 2
```

## [Requirements](#requirements)

- Access to a repository containing packages, likely on the internet.
- A recent version of Ansible. (Tests run on the current, previous and next release of Ansible.)

The following roles can be installed to ensure all requirements are met, using `ansible-galaxy install -r requirements.yml`:

```yaml
---
- robertdebock.bootstrap

```

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://robertdebock.nl/) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/robertdebock/drawings/artifacts/storage.png "Dependency")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/robertdebock):

|container|tags|
|---------|----|
|alpine|all|
|amazon|2018.03|
|el|7, 8|
|debian|buster, bullseye|
|fedora|31, 32|
|opensuse|all|
|ubuntu|focal, bionic, xenial|

The minimum version of Ansible required is 2.8 but tests have been done to:

- The previous version, on version lower.
- The current version.
- The development version.



## [Testing](#testing)

[Unit tests](https://travis-ci.com/robertdebock/ansible-role-storage) are done on every commit, pull request, release and periodically.

If you find issues, please register them in [GitHub](https://github.com/robertdebock/ansible-role-storage/issues)

Testing is done using [Tox](https://tox.readthedocs.io/en/latest/) and [Molecule](https://github.com/ansible/molecule):

[Tox](https://tox.readthedocs.io/en/latest/) tests multiple ansible versions.
[Molecule](https://github.com/ansible/molecule) tests multiple distributions.

To test using the defaults (any installed ansible version, namespace: `robertdebock`, image: `fedora`, tag: `latest`):

```
molecule test

# Or select a specific image:
image=ubuntu molecule test
# Or select a specific image and a specific tag:
image="debian" tag="stable" tox
```

Or you can test multiple versions of Ansible, and select images:
Tox allows multiple versions of Ansible to be tested. To run the default (namespace: `robertdebock`, image: `fedora`, tag: `latest`) tests:

```
tox

# To run CentOS (namespace: `robertdebock`, tag: `latest`)
image="centos" tox
# Or customize more:
image="debian" tag="stable" tox
```

## [License](#license)

Apache-2.0


## [Author Information](#author-information)

[Robert de Bock](https://robertdebock.nl/)

Please consider [sponsoring me](https://github.com/sponsors/robertdebock).
