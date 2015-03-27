# Vagrantizer
A local play to instantiate a m1.medium debian development VM on OpenStack.
Flavor and image can be modified as needed.

## Play variables
The variables to be filled in are:

- `key_name`: The name of the ssh key to inject on the instance.
- `login_tenant_name`: Tenant where the instance should be started.
- `login_username`: OpenStack username
- `login_password`: OpenStack password
- `net-id`: ID of the network to which the instance should be attached.
- `security_groups`: Comma-separated list of security group names to add to this instance.

See [nova_compute](http://docs.ansible.com/nova_compute_module.html) documentation for more info.

## Sample playbook

```yaml
---
- hosts: localhost
  gather_facts: no
  connection: local
  tasks:
    - include: pre_play.yml

- hosts: "{{ target_group }}"
[...]
```

## Playbook invocation

```
$ ansible-playbook playbook.yml -e target_group=significative_groupname
```
