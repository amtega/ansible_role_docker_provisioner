# docker_provisioner

This is an [Ansible](http://www.ansible.com) role to provisione docker images and containers.

## Requirements

- Ansible >= 2.0

## Role Variables

Here is a list of all the default variables for this role, which are also available in `defaults/main.yml`.

```yaml
---
# List of dicts with the images to provisione. See the variable
# docker_provisioner_image_options below for samples of the dict structure.

docker_provisioner_images: []

# List of dicts with the containers to provisione. See the variable
# docker_provisioner_containers_options below for samples of the dict structure.

docker_provisioner_containers: []

# List of ansible groups to add the provisioned containers.

docker_provisioner_groups:
  - docker_provisioner_containers

# Image options to apply if no other ones are specified in the specific image
# dictionary of the docker_provisioner_images variable

docker_provisioner_image_options:
  name: "unnamed"
  dockerfile: "Dockerfile"
  buildargs: {}
  force: false
  path: "."
  rm: true
  state: "present"

# Container options to apply if no other ones are specified in the specific
# container dictionary of the docker_provisioner_containers variable

docker_provisioner_container_options:
  name: "unnamed"
  image: ""
  privileged: true
  state: "started"
  restart: true
  tls: true
  stop_timeout: 1
  tty: true
  expose: ['1-65535']
  command: ""
  env: {}
  links: []
  ansible_user: "root"
  ansible_password: "root"
  volumes: []
  groups:
```

The role also setups dynamically two variables that contain a set of default
images and containers. The variables are, respectively, these ones:

- docker_provisioner_default_images
- docker_provisioner_default_containers

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
