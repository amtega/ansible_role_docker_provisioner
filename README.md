# Ansible docker_provisioner role

This is an [Ansible](http://www.ansible.com) role to provisione docker images and containers.

## Requirements

- [Ansible 2.5+](http://docs.ansible.com/ansible/latest/intro_installation.html)
- [Docker](https://docs.docker.com/engine/installation/). You can use [amtega.docker_engine](https://galaxy.ansible.com/amtega/vagrant_engine/) role to setup it.
- [docker-py](https://github.com/docker/docker-py). Role [amtega.docker_engine](https://galaxy.ansible.com/amtega/vagrant_engine/) above also installs this Python module.

## Role Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

The role setups the following facts:

- `docker_provisioner_containers_facts`: list of dicts with the discovered containers facts.

## Dependencies

None.

## Example Playbook

This is an example playbook:

```yaml
---
- name: docker_provisioner sample
  hosts: localhost
  roles:
    # Load some presets for images and containers

    - role: amtega.docker_presets

    # Provisione images and non ssh based containers

    - role: amtega.docker_provisioner
      docker_provisioner_images: "{{ docker_presets_images }}"
      docker_provisioner_image_state: present
      docker_provisioner_image_force: true
      docker_provisioner_containers: "{{ docker_presets_containers }}"
      docker_provisioner_container_restart: true
      docker_provisioner_container_tty: false
      docker_provisioner_container_state: started

    # Cleanup provisioned containers

    - role: amtega.docker_provisioner

      docker_provisioner_images: []
      docker_provisioner_image_force: true
      docker_provisioner_container_state: absent
      docker_provisioner_containers: "{{ docker_presets_containers }}"
      docker_provisioner_container_restart: true
```

## Testing

Tests are based on vagrant virtual machines. You can setup vagrant engine quickly using the playbook `files/setup.yml` available in the role [amtega.vagrant_engine](https://galaxy.ansible.com/amtega/vagrant_engine).

Once you have vagrant, you can run the tests with the following commands:

```shell
$ cd amtega.docker_provisioner/tests
$ ansible-playbook main.yml
```

## License

Copyright (C) 2017 AMTEGA - Xunta de Galicia

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

- Juan Antonio Valiño García.
