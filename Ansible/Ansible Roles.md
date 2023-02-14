## Structure

:luc_folder_open: roles
	:luc_folder_open: rolename
        :luc_folder_open: tasks
		:luc_folder_open: handlers
		:luc_folder_open: templates
		:luc_folder_open: files
		:luc_folder_open: vars
		:luc_folder_open: defaults
		:luc_folder_open: meta
		:luc_folder_open: library
        :luc_folder_open: module_utils
        :luc_folder_open: lookup_plugins

`tasks` should at minimum contain `main.yml` which will be the entry point for the role.

https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_reuse_roles.html