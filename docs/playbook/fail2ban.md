Introduction
============

This playbook install and config the fail2ban service with iptables or nftables, either of them supported

How to use
==========

For using execute like below:

```bash
ansible-playbook -i <inventory-file> playbook/fail2ban.yml \
  -e host=<host-name-or-group-name>
```

**TIP: According to ansible document, for connect to server(s) you can use below variable:**

* With username and password
    * `ansible_ssh_user`
    * `ansible_ssh_pass`

* With username and ssh-key
    * `ansible_ssh_user`
    * `ansible_ssh_private_key_file`

If your username is not **root** but use in sudo group, you should just use `ansible_sudo_pass` variable.

## Variable

| Name                           | Is require | Default               | Description                                      | Example               |
|--------------------------------|------------|-----------------------|--------------------------------------------------|-----------------------|
| in_fail2ban_log_level          | No         | INFO                  | The log level                                    | INFO                  |
| in_fail2ban_log_target         | No         | /var/log/fail2ban.log | The log target file                              | /var/log/fail2ban.log |
| in_fail2ban_ignore_self        | No         | true                  | Enable/Disable ignore self ip ban                | true                  |
| in_fail2ban_ignore_ips_raw     | No         |                       | Comma-separated list of ips have ignored         | 10.10.10.1,10.10.10.2 |
| in_fail2ban_ignore_ips         | No         |                       | The json format of list of ips have ignored      | -                     |
| in_fail2ban_ban_time           | No         | 10800                 | The ban time of ip (second)                      | 10800                 |
| in_fail2ban_find_time          | No         | 600                   | The scanning time for find fail retries (second) | 600                   |
| in_fail2ban_max_retry          | No         | 3                     | The maximum fail retry                           | 3                     |
| in_fail2ban_configuration      | No         |                       | The json format of fail2ban configuration        | -                     |
| in_fail2ban_jail_configuration | No         |                       | The json format of fail2ban jail configuration   | -                     |

### in_fail2ban_log_level

**Description**: The log level

**Default**: INFO

**Example**:

* -e in_fail2ban_log_level=CRITICAL
* -e in_fail2ban_log_level=ERROR
* -e in_fail2ban_log_level=WARNING
* -e in_fail2ban_log_level=NOTICE
* -e in_fail2ban_log_level=INFO
* -e in_fail2ban_log_level=DEBUG

### in_fail2ban_log_target

**Description**: The log target file

**Default**: INFO

**Example**:

* -e in_fail2ban_log_target=/var/log/fail2ban.log
* -e in_fail2ban_log_target=/path/of/log/file.log

### in_fail2ban_ignore_self

**Description**: Enable/Disable ignore self ip ban

**Default**: true

**Example**:

* -e in_fail2ban_log_target=true
* -e in_fail2ban_log_target=false

### in_fail2ban_ignore_ips_raw

**Description**: Comma-separated list of ips have ignored

**Default**: -

**Example**:

* -e in_fail2ban_log_target=10.10.10.1,10.10.10.2

### in_fail2ban_ignore_ips

**Description**: The json format of list of ips have ignored

**Default**: -

**Example**:

* -e '{"in_fail2ban_ignore_ips": ["10.10.10.1", "10.10.10.2"]}'
* -e @/path/of/my/vars/file.yaml

```yaml
# /path/of/my/vars/file.yaml
in_fail2ban_ignore_ips:
  - 10.10.10.1
  - 10.10.10.2
```

### in_fail2ban_ban_time

**Description**: The ban time of ip (second)

**Default**: 10800

**Example**:

* -e in_fail2ban_ban_time=10800
* -e in_fail2ban_ban_time=600

### in_fail2ban_find_time

**Description**: The scanning time for find fail retries (second)

**Default**: 600

**Example**:

* -e in_fail2ban_find_time=600
* -e in_fail2ban_find_time=300

### in_fail2ban_max_retry

**Description**: The maximum fail retry

**Default**: 3

**Example**:

* -e in_fail2ban_max_retry=3
* -e in_fail2ban_max_retry=5

### in_fail2ban_configuration

**Description**: The json format of list of ips have ignored

**Default**: -

**Example**:

* -e '{"in_fail2ban_configuration": [{"section": "default", option": "key1", "value": "value1"}, {"section": "default", option": "key2", "value": "value2"}]}'
* -e @/path/of/my/vars/file.yaml

```yaml
# /path/of/my/vars/file.yaml
in_fail2ban_configuration:
  - section: "default"
    option: "key1"
    value: "value1"
  - section: "default"
    option: "key2"
    value: "value2"
```

### in_fail2ban_jail_configuration

**Description**: The json format of fail2ban jail configuration

**Default**: -

**Example**:

* -e '{"in_fail2ban_jail_configuration": [{"section": "default", option": "key1", "value": "value1"}, {"section": "default", option": "key2", "value": "value2"}]}'
* -e @/path/of/my/vars/file.yaml

```yaml
# /path/of/my/vars/file.yaml
in_fail2ban_jail_configuration:
  - section: "default"
    option: "key1"
    value: "value1"
  - section: "default"
    option: "key2"
    value: "value2"
```