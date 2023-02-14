Single files that specify a set of operations

Run with `ansible-playbook FILENAME.YML`

`````ad-info
title: Common `ansible-playbook` CLI flags
collapse: true

| Flag             | Meaning                                |
| ---------------- | -------------------------------------- |
| `-f 10`            | Run on 10 hosts in parallel            |
| `--verbose`        | Extra verbosity                        |
| `-C` / `--check`     | Test run, guess at what would change   |
| `-D` / `--diff`      | Show diffs                             |
| `-l SUBSET`        | Limit to subset of hosts               |
| `--check-syntax` | Do not run; check playbook syntax only |
`````


`````ad-info
title: Sample playbook
collapse: true
```yaml
---
- name: Test playbook for demo purposes
  hosts: localhost
  gather_facts: false
  tasks:

  - name: Print a message
    debug: msg="Hello, world!"

  - name: Copy git configuration
    copy:
      src: "./master.gitconfig"
      dest: "~/.gitconfig"
```
`````


# Links
[Intro to playbooks](https://docs.ansible.com/ansible/latest/user_guide/playbooks_intro.html)
