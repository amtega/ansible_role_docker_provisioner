# Change Log

## 2017-03-09

- Initial release.

## 2017-03-23

- Addded support for container volumes.
- Fixed CentOS 7 image and container.
- Create separated folders and files for images and containers defaults.

## 2017-03-24

- Refactored default variables structure.
- Improved tests.
- Improved documentation.

## 2017-03-27

- Refactored config variables to support random container names.
- Improved tests.
- Improved label during container setup.

## 2017-05-08

- Added role variables to decouple random name generation

## 2017-05-12

- Refactored random container name feature.

## 2017-05-18

- Moved random container name to docker_role_tester role.
- Added missing image parameter into defaults/main.yml
- Handled known_hosts entries of provisioned containers.

## 2017-05-19

- Refactored default images/containers functionality.

## 2017-06-01

- Fixed some minor bugs.
- Fixed unit tests.
- Improved documentation in README.md

## 2017-06-05

- Improved documentation in README.md file.

## 2017-06-08

- Containers ssh host key are added to known_hosts file.

## 2017-06-15

- Improved SSH public keys management.
- Improve role structure.

## 2017-06-16

- Added support for labels attribute in containers.

## 2017-09-25

- Improved dry run support.

## 2017-09-29

- Refactored include directives by include_tasks / import_tasks.
- Updated documentation.

## 2017-10-04

- Now by privileged mode is disabled by default.

## 2017-10-16

- All UDP ports now are exposed by default.
