# Ansible role [confluence](https://galaxy.ansible.com/ui/standalone/roles/buluma/confluence/documentation)

Ansible Role for Atlassian Confluence Installation

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-confluence/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-confluence/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-confluence.svg)](https://github.com/buluma/ansible-role-confluence/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-confluence.svg)](https://github.com/buluma/ansible-role-confluence/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-confluence.svg)](https://github.com/buluma/ansible-role-confluence/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/confluence)](https://galaxy.ansible.com/ui/standalone/roles/buluma/confluence/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-confluence/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- hosts: all
  remote_user: root
  become: true
  roles:
    - role: buluma.confluence
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-confluence/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: yes
  gather_facts: no

  roles:
    - role: buluma.bootstrap
    - role: buluma.java
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-confluence/blob/master/defaults/main.yml):

```yaml
---

# PostgreSQL JDBC release.
postgresql_jdbc_release: "42.3"

# PostgreSQL JDBC version.
postgresql_jdbc_version: "{{ _postgresql_jdbc_version[postgresql_jdbc_release] }}"

# PostgreSQL JDBC download details.
postgresql_jdbc_download: "{{ _postgresql_jdbc_download[postgresql_jdbc_version] }}"

# Confluence release.
confluence_release: "7.17"

# Confluence version.
confluence_version: "{{ _confluence_version[confluence_release] }}"

# Confluence download details.
confluence_download: "{{ _confluence_download[confluence_version] }}"

# Owner and group for Confluence.
confluence_owner: "confluence"
confluence_group: "confluence"

# Confluence home directory.
confluence_home: "/var/atlassian/application-data/confluence"

# Confluence installation directory.
confluence_catalina: "/opt/atlassian/confluence"

# JVM minimal and maximum memory usage.
confluence_jvm_minimum_memory: "2048m"
confluence_jvm_maximum_memory: "2048m"

# Proxy and context path setup.
confluence_catalina_connector_proxyname: ~
confluence_catalina_connector_proxyport: ~
confluence_catalina_connector_scheme: "http"
confluence_catalina_connector_secure: "false"
confluence_catalina_context_path: ~

# Atlassian Support recommended JVM arguments.
confluence_jvm_support_recommended_args: >-
  -Datlassian.plugins.enable.wait=300
  -XX:+UnlockExperimentalVMOptions
  -XX:+UseCGroupMemoryLimitForHeap
  -XX:MaxRAMFraction=1

# Session timeout (in minutes).
confluence_session_timeout: "120"
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-confluence/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.java](https://galaxy.ansible.com/buluma/java)|[![Ansible Molecule](https://github.com/buluma/ansible-role-java/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-java/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-java.svg)](https://github.com/shadowwalker/ansible-role-java)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-confluence/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|all|
|[EL](https://hub.docker.com/r/buluma/enterpriselinux)|7|
|[opensuse](https://hub.docker.com/r/buluma/opensuse)|all|
|[Debian](https://hub.docker.com/r/buluma/debian)|all|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|all|

The minimum version of Ansible required is 4.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-confluence/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-confluence/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-confluence/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)
