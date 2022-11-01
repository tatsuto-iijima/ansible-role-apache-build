# apache_build

![CI](https://github.com/tatsuto-iijima/ansible-role-apache-build/actions/workflows/molecule.yml/badge.svg)

Ansible role that builds Apache from source.

## Requirements

The supported Ansible version are as follows:
- 2.13

The Apache versions that can be installed with this Role are as follows:
- 2.4

The supported platforms are as follows:
- CentOS 7
- CentOS 8
- RHEL 8

## Role Variables

Required:

- `apache_build_version`: string

  Version of Apache to install (ex. `2.4.54`)

Optional:

- `apache_build_unarchive_remote_src`: boolean (default: no)

  Whether to download the Apache sources on a remote server

- `apache_build_unarchive_dest`: path (default: /usr/local/src)

  Apache unarchive dest

- `apache_build_configure_option`: list / elements=string (default: [])

  Apache config option

- `apache_build_make_target`: list / elements (default: [ { target: all, params: {} }, { target: install, params: {} } ])
  
  Apache make target

## Dependencies

Nothing.

## Example Playbook

An example of using this role is as follows:

```
- hosts: servers
  roles:
      - role: tatsuto_iijima.apache_build
        apache_build_version: "2.4.54"
        apache_build_config_option:
          - "--with-ssl=/usr/local/openssl"
          - "LDFLAGS='-Wl,-rpath,/usr/local/openssl/lib'"
```

## License

Apache License, Version 2.0
