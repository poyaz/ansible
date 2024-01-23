Introduction
============

This playbook install and config the docker service

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

Or using prompt flag:

* `-k, --ask-pass`
* `-K, --ask-become-pass`

**TIP: If the `sudo` is not installed in server, You can use `su` command for become method**

```bash
ansible-playbook ... --become-method su ...
```

If your username is not **root** but use in sudo group, you should just use `ansible_sudo_pass` variable.

## Variable

| Name                   | Is require | Default | Description                                                                             | Example             |
|------------------------|------------|---------|-----------------------------------------------------------------------------------------|---------------------|
| in_proxy_addr          | No         |         | The proxy server address                                                                | http://proxy-server |
| in_http_proxy          | No         |         | The http proxy server address                                                           | http://proxy-server |
| in_https_proxy         | No         |         | The https proxy server address                                                          | http://proxy-server |
| in_remove_proxy_at_end | No         | false   | Remove proxy from all environment and config files (after finish all tasks in playbook) | true                |
| in_force_remote_proxy  | No         | false   | Forcing to remove all proxy from all environment and config files at beginning          | true                |

### in_proxy_addr

**Description**: The proxy server address

If this variable is set, then override `in_http_proxy` and `in_https_proxy`

**Default**: -

**Example**:

* -e in_proxy_addr=http://proxy-server:
* -e in_proxy_addr=http://proxy-server:8080
* -e in_proxy_addr=http://127.0.0.1:8080

### in_http_proxy

**Description**: The http proxy server address

**Default**: -

**Example**:

* -e in_http_proxy=http://proxy-server:
* -e in_http_proxy=http://proxy-server:8080
* -e in_http_proxy=http://127.0.0.1:8080

### in_https_proxy

**Description**: The https proxy server address

**Default**: -

**Example**:

* -e in_https_proxy=http://proxy-server:
* -e in_https_proxy=http://proxy-server:8080
* -e in_https_proxy=http://127.0.0.1:8080

### in_remove_proxy_at_end

**Description**: Remove proxy from all environment and config files (after finish all tasks in playbook)

**Default**: false

**Example**:

* -e in_remove_proxy_at_end=true

### in_force_remote_proxy

**Description**: Forcing to remove all proxy from all environment and config files at beginning

**Default**: false

**Example**:

* -e in_force_remote_proxy=true