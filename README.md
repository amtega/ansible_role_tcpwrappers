# Ansible tcpwrappers role

This is an [Ansible](http://www.ansible.com) role which configures TCP Wrappers security framework through `/etc/hosts.allow` and `/etc/hosts.deny` files.

## Requirements

[Ansible 2.7+](http://docs.ansible.com/ansible/latest/intro_installation.html)

## Role Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

## Example Playbook

This is an example playbook:

```yaml
---

- hosts: all
  roles:    
    - role: amtega.tcpwrappers
      vars:
        tcpwrappers_allow:
          - daemons:
              - ssh
              - ftp
            clients:
              - localhost
            state: present

          - daemons:
              - ssh
              - ftp
            clients:
              - LOCAL
            state: present

        tcpwrappers_deny:
          - daemons:
              - ALL
            clients:
              - ALL
            state: present

```

## Testing

Tests are based on docker containers. You can setup docker engine quickly using the playbook `files/setup.yml` available in the role [amtega.docker_engine](https://galaxy.ansible.com/amtega/docker_engine).

Once you have docker, you can run the tests with the following commands:

```shell
$ cd amtega.tcpwrappers/tests
$ ansible-playbook main.yml
```

## License

Copyright (C) 2019 AMTEGA - Xunta de Galicia

This role is free software: you can redistribute it and/or modify it under the terms of:

GNU General Public License version 3, or (at your option) any later version; or the European Union Public License, either Version 1.2 or – as soon they will be approved by the European Commission ­subsequent versions of the EUPL.

This role is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details or European Union Public License for more details.

## Author Information

- Carlos Chedas Fernández
- Daniel Sánchez Fábregas
- Juan Antonio Valiño García
