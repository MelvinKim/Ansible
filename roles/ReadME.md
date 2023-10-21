##### Ways to create ansible roles:
1. Using the ansible galaxy command
```
ansible-galaxy init <role-name>
```
2. Manually - creating only the folders you need.

- Ansible searches for roles in:
1.  /etc/ansible/roles
2. roles directory relative to the playbook file

- Variables
1. Role's default variables have the lowest precedence.
2. Roles's var override most of the other defined variables.