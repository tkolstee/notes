## Install
`python3 -m pip install --user ansible`

## Configuration
`````ad-info
title: `/etc/ansible/ansible.cfg`
```
inventory = /etc/ansible/hosts
```
`````

`````ad-info
title: `/etc/ansible/hosts`
```ini
localhost
node1
node2
```
`````

`hosts` should list all nodes you want to manage.
Establish SSH key authentication with all hosts

## Testing
```bash
# ansible -m ping all

localhost | SUCCESS => {
    "changed": false,
    "ping": "pong"
}
```

