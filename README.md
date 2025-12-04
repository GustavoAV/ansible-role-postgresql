# Ansible Role - PostgreSQL

Ansible role to setup Docker.

- [Ansible Role - PostgreSQL](#ansible-role---postgresql)
  - [Requirements](#requirements)
  - [Usage](#usage)
  - [Development](#development)
  - [References](#references)

## Requirements

Requirements for using this role:

- Operational system: Debian 11+, Ubuntu 22+ or RedHat 9+

## Usage

> The `defaults/main.yml` file has all the available parameters and their usage descriptions.

Create a `requirements.yml` file with the content below and install with `ansible-galaxy install -r requirements.yml`.

```yaml
---
roles:
  - name: gustavoav.postgresql
    src: git+https://github.com/GustavoAV/ansible-role-postgresql.git
```

Create a playbook (e.g: `setup_postgresql.yml`) and apply with `ansible-playbook setup_postgresql.yml`.

```yaml
---
- name: Install PostgreSQL
  hosts: all
  become: true
  roles: [gustavoav.postgresql]
```

## Development

> First, install **docker**.

To setup your development environment, run the commands below.

```bash
# Install UV
curl -LsSf https://astral.sh/uv/install.sh | sh
source ~/.local/bin/env

# Install Ansible tools
uv tool install ansible-dev-tools \
  --with-executables-from=ansible-core,ansible-lint \
  --with-requirements requirements.txt

# Validate
ansible --version
molecule --version
```

And then, to test everything:

```bash
molecule test
```

## References

- [PostgreSQL Docs - Install](https://www.postgresql.org/download/)
