# Facts Ansible Role

This role sets custom [Ansible facts](http://docs.ansible.com/ansible/playbooks_variables.html#information-discovered-from-systems-facts) that other roles or playbooks can utilize with [conditionals](http://docs.ansible.com/ansible/playbooks_conditionals.html). It should be applied before any other roles or playbooks that depend on these custom facts.

## Facts

Please refer to the [defaults/main.yml](https://github.com/idi-ops/ansible-facts/blob/master/defaults/main.yml) file for a list of variables and the facts that they set.

## Examples

Here are two examples of tasks using custom platform-specific facts. If a Fedora environment is detected the ``dnf`` module will be used to install a package:

```
- name: Install Node.js on Fedora
  dnf:
    name: nodejs
    state: present
  when: is_fedora
```

If a CentOS environment is detected the ``yum`` module will be used to install a package:

```
- name: Install Node.js on CentOS
  yum:
    name: nodejs
    state: present
  when: is_centos
```
