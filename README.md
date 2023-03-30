ansible-truenas-v2
=========

An Ansible role to manage TrueNAS **CORE** via API v2

NOTE: Not everything from API was implement here. 

Testing
-------

Think twice before run against your production environment.
I am not responsible for any loss data!
This role is still under extensive testing.

Requirements
------------

Read `requirements.txt`.

Role Variables
--------------

Check `dafaults/main.yml` for more information about variables.

Role Tags
---------

Role contain such tasks with such tags, use them to apply changes:

```
    tasks:
      ansible-truenas-v2 : Groups                TAGS: [truenas_groups]
      ansible-truenas-v2 : Services              TAGS: [truenas_services]
      ansible-truenas-v2 : Users                 TAGS: [truenas_users]
      ansible-truenas-v2 : Disks                 TAGS: [truenas_disks, truenas_unused_disks]
      ansible-truenas-v2 : Pools                 TAGS: [truenas_pools]
      ansible-truenas-v2 : Datasets              TAGS: [truenas_datasets]
      ansible-truenas-v2 : Systems               TAGS: [truenas_systems]
      ansible-truenas-v2 : Shares                TAGS: [truenas_shares]
      ansible-truenas-v2 : Jails                 TAGS: [truenas_jails]
      ansible-truenas-v2 : Tunables              TAGS: [truenas_tunables]
      ansible-truenas-v2 : Init Shutdown Scripts TAGS: [truenas_scripts]
      ansible-truenas-v2 : Plugins               TAGS: [truenas_plugins]
```

Example Playbook
----------------

```
 - hosts: my-truenas-core-host
   
   become: false

   gather_facts: false

   roles:
    - role: ansible-truenas-v2

```

```
# as a first step, lets create groups
ansible-playbook ansible-truenas-v2.yml -i inventories/my-hosts/inventory.yml -t truenas_groups

# now when we have groups, lets add users
ansible-playbook ansible-truenas-v2.yml -i inventories/my-hosts/inventory.yml -t truenas_users

# it will be good to have Pool
ansible-playbook ansible-truenas-v2.yml -i inventories/my-hosts/inventory.yml -t truenas_pools

# without Datasets it will be useless
ansible-playbook ansible-truenas-v2.yml -i inventories/my-hosts/inventory.yml -t truenas_datasets

# and so on
```

License
-------

MIT

RoadMap
-------

TODO:
- [ ] Cleanup and make the "same" templates
- [ ] Share tasks for AFP
- [ ] Share tasks for ISCI
- [ ] Share tasks for WebDAV
- [ ] Share tasks for NFS
- [ ] VM tasks

Author Information
------------------
Dmitriy Matveev
