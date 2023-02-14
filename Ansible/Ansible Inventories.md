## Commands

`ansible-inventory` `[--list|--graph|--host HOST]`

## Inventory Files
Inventory files can be in INI or YAML syntax
`````ad-info
collapse: true
title: INI Inventory File Example
```ini
file-server
print-server

[web]
www[1:10]  ansible_port=222

[mail]
smtp[1:2]

[external]
ns[1:2]
firewall

[external:children]
web
mail

[redundancy_group_a]
www[1:10:2]
smtp1
ns1

[redundancy_group_b]
www[2:10:2]
smtp2
ns2

[workstations]
workstation-[001:100]

[mail:vars]
smtp_port=25
```
`````

`````ad-info
title: YAML Inventory File Example
collapse: true
```yaml
all:
  children:
    external:
      children:
        mail:
          hosts:
            smtp[1:2]: {}
          vars:
            smtp_port: 25
        web:
          hosts:
            www[1:10]:
              ansible_port: 222
      hosts:
        firewall: {}
        ns[1:2]: {}
    redundancy_group_a:
      hosts:
        ns1: {}
        smtp1: {}
        www[1:10:2]: {}
    redundancy_group_b:
      hosts:
        ns2: {}
        smtp2: {}
        www[2:10:2]: {}
    ungrouped: {}
    workstations:
      hosts:
        workstation-[001:100] {}

```
`````

## Inventory Directories
- Config `INVENTORY_IGNORE_EXTS`  specifies extensions to ignore
- Files processed in ASCIIbetical order
- Can include static inventory files or inventory scripts

## Dynamic Inventory

### Plugins
`ansible-doc -t inventory --list` to see options
`ansible-doc -t inventory plugin_name` to see plugin docs

### Inventory Scripts
Should return a JSON inventory when run

## Groups
- Groups can be nested
- Hosts belong to two or more groups (Implicit `all` and `ungrouped` if no other groups)

## Variables
- Can be specified per-host (inline) or per-group in inventory
- Can also be specified in separate files (`host_vars`, `group_vars`)
- Precedence from lowest to highest (configurable with `ansible_group_priority` setting)
	- `all` group
	- parent group
	- child group
	- host

`````ad-info
title: Variable File Layout
collapse: true
Variables can be specified as name:value pairs in JSON or YAML files
These should be stored relative to the inventory (`hosts` in this case)
```
/etc/ansible/
  hosts
  group_vars/
    groupname1.yml
    groupname2.yml
  host_vars/
    hostname1/
      db_settings.json
      network_settings.json
    hostname2.yml
```
`````

`````ad-info
collapse: true
title: Inventory variables
| Parameter                    | Description                                  |
| ---------------------------- | -------------------------------------------- |
| ansible_connection           | Connection type                              |
| ansible_host                 | Hostname to connect to                       |
| ansible_port                 | SSH port number                              |
| ansible_user                 | SSH username to use                          |
| ansible_ssh_pass             | SSH password to use                          |
| ansible_ssh_private_key_file | Private key file used by SSH                 |
| ansible_ssh_common_args      | Append to ssh, scp, sftp command line        |
| ansible_sftp_extra_args      | Append to sftp command line                  |
| ansible_scp_extra_args       | Append to scp command line                   |
| ansible_ssh_extra_args       | Append to ssh command line                   |
| ansible_ssh_pipelining       | Whether or not to use SSH pipelining         |
| ansible_ssh_executable       | Executable to use for ssh                    |
| ansible_become               | User to become - force priv esc              |
| ansible_become_method        | PrivEsc method                               |
| ansible_become_user          | User to become                               |
| ansible_become_pass          | Password for PrivEsc method                  |
| ansible_become_exe           | Executable for PrivEsc method selected       |
| ansible_become_flags         | Flags passed to PrivEsc method               |
| ansible_shell_type           | Can set to csh or fish for non-Bourne shells |
| ansible_python_interpreter   | Target host python path                      |
| ansible_xx_interpreter       | Set interpreter for ruby, perl, etc.         |
| ansible_shell_executable     | Override /bin/sh                             |


ansible_connection can support: smart, ssh, paramiko, local, and docker.
`````

# Links
[How to build your inventory](https://docs.ansible.com/ansible/latest/user_guide/intro_inventory.html)
[Working with Inventory](https://docs.ansible.com/ansible/2.7/user_guide/intro_inventory.html)
[Working With Dynamic Inventory](https://docs.ansible.com/ansible/2.7/user_guide/intro_dynamic_inventory.html#intro-dynamic-inventory)
[Inventory Plugins](https://docs.ansible.com/ansible/2.7/plugins/inventory.html#inventory-plugins)
[Developing dynamic inventory](https://docs.ansible.com/ansible/2.7/dev_guide/developing_inventory.html#developing-inventory)
