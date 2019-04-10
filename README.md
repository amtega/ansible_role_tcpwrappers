# Ansible tcpwrappers role

This is an [Ansible](http://www.ansible.com) role which configures TCP Wrappers security framework through `/etc/hosts.allow` and `/etc/hosts.deny` files.

## Requirements

[Ansible 2.7+](http://docs.ansible.com/ansible/latest/intro_installation.html)

## Role Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

## Dependencies

None.

## Example Playbook

This is an example playbook:

```yaml
---

- hosts: all
  roles:    
    - role: amtega.xinetd_service
      # list of services to deny access
      tcpwrappers_deny:
        # service_tag:
        #   denied_service_name: name of the service
        #   denied_host_list: list of host to deny access
        ftpd:
          denied_service_name: "in.ftpd"
          denied_hosts_list:
            - ALL
      # list of services to allow access
      tcpwrappers_allow:
        ALL:
          allowed_service_name: "ALL"
          allowed_hosts_list: ["localhost","LOCAL"]

        xinetd:
          allowed_service_name: "xinetd"
          allowed_hosts_list:
            - ALL
            - hosts2
```
## Testing

Test are based on docker containers. You can run the tests with the following commands:

```shell
$ cd amtega.tcpwrappers/tests
$ ansible-playbook main-docker.yml
```

If you have docker engine configured you can avoid running dependant 'docker_engine' role (that usually requries root privileges) with the following commands:

```shell
$ cd amtega.tcpwrappers/tests
$ ansible-playbook --skip-tags "role::docker_engine" main-docker.yml

If you dont use docker containers:

```shell
$ cd amtega.xinetd_service/tests
$ ansible-playbook -u [ssh_user] -kK main.yml



## License

Copyright (C) <YEAR> AMTEGA - Xunta de Galicia

This role is free software: you can redistribute it and/or modify
it under the terms of:
GNU General Public License version 3, or (at your option) any later version;
or the European Union Public License, either Version 1.2 or – as soon
they will be approved by the European Commission ­subsequent versions of
the EUPL;

This role is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details or European Union Public License for more details.

## Author Information

- author_name 1.
- author_name N.
