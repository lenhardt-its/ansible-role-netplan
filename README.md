# Ansible Role: Netplan

[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![GitHub tag](https://img.shields.io/github/tag/OnkelDom/ansible-role-netplan.svg)](https://github.com/OnkelDom/ansible-role-netplan/tags)
[![GitHub issues](https://img.shields.io/github/issues/OnkelDom/ansible-role-netplan)](https://github.com/OnkelDom/ansible-role-netplan/issues)
[![GitHub license](https://img.shields.io/github/license/OnkelDom/ansible-role-netplan)](https://github.com/OnkelDom/ansible-role-netplan/blob/master/LICENSE)

## Description

Install and manage network interfaces with netplan using ansible.

## Requirements

- Ansible >= 2.6 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `netplan_file` | "99_ansible.yaml" | Netplan config file inside netplan_path |
| `netplan_path` | "/etc/netplan" | Netplan file path |
| `netplan_config` | {} | Default interface config |
| `netplan_enabled` | true | Enable/Disable |
| `netplan_packages` | "netplan.io,nplan" | Required Packages |
| `netplan_renderer` | "networkd" | Netplan renderer |
| `netplan_version ` | 2 | Netplan version |
| `netplan_wipe` | false | Wipe all other configs|

## Example
```yaml
netplan_config:
  network:
    ethernets:
      eno1:
        addresses:
          - 192.168.1.10/24
        gateway4: 192.168.1.1
        nameservers:
          search: [example.com]
          addresses: [1.1.1.1, 8.8.8.8]
      eno2:
        dhcp4: false
        dhcp6: false
        optional: true
```
### Playbook

```yaml
- hosts: all
  roles:
    - ansible-role-alertmanager
```

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
