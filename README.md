# Ansible tcpwrappers role

This is an [Ansible](http://www.ansible.com) role which configures TCP Wrappers security framework through `/etc/hosts.allow` and `/etc/hosts.deny` files.

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

Tests are based on [molecule with docker containers](https://molecule.readthedocs.io/en/latest/installation.html).

```shell
cd amtega.tcpwrappers

molecule test
```

## License

Copyright (C) 2022 AMTEGA - Xunta de Galicia

This role is free software: you can redistribute it and/or modify it under the terms of:

GNU General Public License version 3, or (at your option) any later version; or the European Union Public License, either Version 1.2 or – as soon they will be approved by the European Commission ­subsequent versions of the EUPL.

This role is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details or European Union Public License for more details.

## Author Information

- Carlos Chedas Fernández
- Daniel Sánchez Fábregas
- Juan Antonio Valiño García
