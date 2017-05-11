# docker_provisioner

This is an [Ansible](http://www.ansible.com) role to provisione docker images and containers.

## Requirements

- Ansible >= 2.0

## Role Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

The role also setups dynamically two variables that contain a set of default images and containers. The variables are, respectively, these ones:

- docker_provisioner_default_images
- docker_provisioner_default_containers

The role provides the `randomize_names` filter that allow the generation of a set of contaniners/images to use with the docker_provisioner_containers/docker_provisioner_images variables, but with the names replaced by random strings.

## Dependencies

- docker_engine

## Example Playbook

This is an example playbook:

```yaml
---

- hosts: all
  roles:
    - docker_provisioner
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
