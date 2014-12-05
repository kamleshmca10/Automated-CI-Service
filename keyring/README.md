keyring
==================

This folder is where any SSH keys should be created
to help facilitate authentication for Jenkins,
GIT & SSH or other services.

## Docker templates
When working with any of the Docker templates
a symlink in the `docker-templates/common/keys`
points to this folder so any `*.pub` & `known_hosts`
files get copied to the container on build.

Prior to building a new or existing Dockerfile
you should run the `./populate-common` tool.

## Ansible playbook system
When using ansible to perform management any
keys to be used for authentication are also
to be stored here. For example:

```yml
# file: ansible-toolkit/host_vars/node-01
- authorized_key: user=user-01
                  key="{{ lookup('file', '../../keyring/id_rsa.pub') }}'
                  path='/etc/ssh/authorized_keys/user-01'
                  manage_dir=no
```
