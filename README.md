# Ansible docker_provisioner role

This is an [Ansible](http://www.ansible.com) role to provisione docker images and containers.

## Requirements

- Ansible >= 2.4

## Role Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

## Dependencies

- docker_engine

## Example Playbook

This is an example playbook:

```yaml
---
- name: docker_provisioner sample
  hosts: localhost
  roles:
    # Load some presets for images and containers

    - role: docker_presets

    # Provisione images and non ssh based containers

    - role: docker_provisioner
      docker_provisioner_images: "{{ docker_presets_images }}"
      docker_provisioner_image_state: present
      docker_provisioner_image_force: true
      docker_provisioner_containers: "{{ docker_presets_containers }}"
      docker_provisioner_container_restart: true
      docker_provisioner_container_tty: false
      docker_provisioner_container_state: started

    # Cleanup provisioned containers

    - role: docker_provisioner

      docker_provisioner_images: []
      docker_provisioner_image_force: true
      docker_provisioner_container_state: absent
      docker_provisioner_containers: "{{ docker_presets_containers }}"
      docker_provisioner_container_restart: true
```

## Testing

Test are based on docker containers. You can run the tests with the following commands:

```shell
$ cd docker_provisioner/test
$ ansible-playbook main.yml
```

If you have docker engine configured you can avoid running dependant 'docker_engine' role (that usually requries root privileges) with the following commands:

```shell
$ cd docker_provisioner/test
$ ansible-playbook --skip-tags "role::docker_engine" main.yml
```

## License

Not defined.

## Author Information

- Juan Antonio Valiño García ([juanval@edu.xunta.es](mailto:juanval@edu.xunta.es)). Amtega - Xunta de Galicia
