# Ansible role rsyslog

Managing rsyslog.

- [Ansible role rsyslog](#ansible-role-rsyslog)
  - [License](#license)
  - [Author Information](#author-information)
  - [Requirements](#requirements)
  - [Dependencies](#dependencies)
  - [Compatibility](#compatibility)
  - [Role Variables](#role-variables)
  - [Example Playbook](#example-playbook)
  - [Useful shell commands](#useful-shell-commands)
  - [Additional documentation resources](#additional-documentation-resources)
  - [Testing with Molecule](#testing-with-molecule)
  - [CI/CD with Travis CI](#cicd-with-travis-ci)
  - [Useful links](#useful-links)

## License

MIT / BSD

## Author Information

- Made and maintained by: [Kasra Amirsarvari](https://www.linkedin.com/in/caseraw)
- Ansible Galaxy community author: <https://galaxy.ansible.com/caseraw>
- Dockerhub community user: <https://hub.docker.com/u/caseraw>

## Requirements

- Ensure a package manager is available and configured with the correct package sources and repositories.
- Ensure privileged permissions are set for the user executing this role to:
  - Install packages.
  - Manage service settings and configurations.

## Dependencies

N/A

## Compatibility

Compatible with the following list of operating systems:

- CentOS 7
- CentOS 8
- RHEL 7.x
- RHEL 8.x

## Role Variables

| Variable name | Description |
|---------------|-------------|
| role_rsyslog_packages | A list of packages to install. |
| role_rsyslog_conf_file | Rsyslog configuration file. |

## Example Playbook

```yaml
---
- name: Manage rsyslog
  become: True
  gather_facts: True
  tasks:
    - import_role:
        name: ansible_role_rsyslog
      vars:
        role_rsyslog_packages:
          - rsyslog
        role_rsyslog_conf_file:
          dest: /etc/rsyslog.conf
          src: auditd_conf.j2
          owner: root
          group: root
          mode: '0640'
          parameters:
            - 'some meaningful configuration value'
            - 'some meaningful configuration value'
            - 'some meaningful configuration value'

...
```

## Useful shell commands

N/A

## Additional documentation resources

- `/usr/share/doc/rsyslog-*/rsyslog_conf.html`
- <http://www.rsyslog.com/doc/troubleshoot.html>

## Testing with Molecule

This role is locally tested with the use of [Molecule](https://molecule.readthedocs.io/en/latest/), the configuration is located at: [molecule/default](molecule/default).  
The Molecule tests are run (using the [docker driver](https://molecule.readthedocs.io/en/latest/configuration.html#docker)) on [Dockerhub images](https://hub.docker.com/u/caseraw) built for this purpose:

- [CentOS](https://hub.docker.com/r/caseraw/ansible-molecule-centos)
- [Fedora](https://hub.docker.com/r/caseraw/ansible-molecule-fedora)

## CI/CD with Travis CI

This role uses [Travis CI](https://travis-ci.org/) to run online tests with the use of [Molecule](https://molecule.readthedocs.io/en/latest/) and pushes notifications to import the role into [Ansible Galaxy](https://galaxy.ansible.com/) once the tests are successful. The Travis CI configuration is located at the root of the Ansible role [.travis.yml](.travis.yml)

## Useful links

- GitHub repository: <https://github.com/Caseraw/ansible_role_rsyslog>
- Travis CI build status: <https://travis-ci.org/Caseraw/ansible_role_rsyslog>
- Ansible Galaxy role: <https://galaxy.ansible.com/caseraw/ansible_role_rsyslog>
