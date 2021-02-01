# Ansible Role: UFW

[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![GitHub tag](https://img.shields.io/github/tag/OnkelDom/ansible-role-ufw.svg)](https://github.com/OnkelDom/ansible-role-ufw/tags)
[![GitHub issues](https://img.shields.io/github/issues/OnkelDom/ansible-role-ufw)](https://github.com/OnkelDom/ansible-role-ufw/issues)
[![GitHub license](https://img.shields.io/github/license/OnkelDom/ansible-role-ufw)](https://github.com/OnkelDom/ansible-role-ufw/blob/master/LICENSE)

## Description

Install and configure ufw using ansible.

## Requirements

- Ansible >= 2.10 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `ufw_rules` | [defaults](defaults/main.yml) | UFW Rules |
| `ufw_manage_config` | true | Manage UFW config file |
| `ufw_config` | [defaults](defaults/main.yml) | UFW config |


## Example
```yaml
ufw_rules:
  # Set loggin
  - logging: "full"
  # Allow OpenSSH
  - rule: allow
    name: OpenSSH
  # Delete OpenSSH rule
  - rule: allow
    name: OpenSSH
    delete: true
    # Allow all access to tcp port 80
    - rule: allow
    to_port: '80'
    proto: tcp
# Manage the configuration file
ufw_manage_config: true
# Configuration object passed to the configuration file
ufw_config:
  IPV6: "yes"
  DEFAULT_INPUT_POLICY: DROP
  DEFAULT_OUTPUT_POLICY: ACCEPT
  DEFAULT_FORWARD_POLICY: DROP
  DEFAULT_APPLICATION_POLICY: SKIP
  MANAGE_BUILTINS: "no"
  IPT_SYSCTL: /etc/ufw/sysctl.conf
  IPT_MODULES: ""
```
### Playbook

```yaml
- hosts: localhost
  vars:
    ufw_rules:
      # Set loggin
      - logging: "full"
      # Allow OpenSSH
      - rule: allow
        name: OpenSSH
      # Delete OpenSSH rule
      - rule: allow
        name: OpenSSH
        delete: true
      # Allow all access to tcp port 80
      - rule: allow
        to_port: '80'
        proto: tcp
    # Manage the configuration file
    ufw_manage_config: true
    # Configuration object passed to the configuration file
    ufw_config:
      IPV6: "yes"
      DEFAULT_INPUT_POLICY: DROP
      DEFAULT_OUTPUT_POLICY: ACCEPT
      DEFAULT_FORWARD_POLICY: DROP
      DEFAULT_APPLICATION_POLICY: SKIP
      MANAGE_BUILTINS: "no"
      IPT_SYSCTL: /etc/ufw/sysctl.conf
      IPT_MODULES: ""
  roles:
    - ansible-role-ufw
```

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
