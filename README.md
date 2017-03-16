# docker_provisioner

This is an [Ansible](http://www.ansible.com) role to provisione docker images and containers.

## Requirements

- Ansible >= 2.0

## Role Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`. The file `vars/main.yml` contains full examples of these variable structures.

```yaml
---

# List of dicts with the images to provisione. See vars/main.yml examples.

#docker_provisioner_images:

# List of dicts with the containers to provisione. See vars/main.yml examples.

#docker_provisioner_containers:

# List of groups to add the provisioned containers. See vars/main.yml examples.

#docker_provisioner_groups:
```

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

```shell
$ cd docker_provisioner/test
$ ansible-playbook main.yml
```

## License

Not defined.

## Author Information

- Juan Antonio Valiño García ([juanval@edu.xunta.es](mailto:juanval@edu.xunta.es)). Amtega - Xunta de Galicia
