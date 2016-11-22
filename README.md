Django Channels worker
======================

Ansible role for running django-channel workers in supervisor

Requirements
------------

- Debian
- Django app

Role Variables
--------------

- `app` - app label (inherited from `django_common` role)
- `program_name` - name for supervisor entry defaults to `{{ app }}`
- `threads` - number of threads to start for given worker defaults to `{{ ansible_process_vcpus }}`
- `priority` - priority to start/stop entry in supervisor instance
- `supervisor_conf_tpl` - supervisor's config template to customize (defaults to: [templates/_default_supervisor.conf.j2](https://github.com/xkoralsky/ansible_django_channels_worker/blob/master/templates/_default_supervisor.conf.j2))
- `channel_layer_name` - channel layer name mentioned in django app's settings (if different than `default`)
- `only_channels` - list of channels to listen to
- `exclude_channels` - list of channels to ignore
- `verbosity` - 1,2 or 3 logging verbosity level

Dependencies
------------

- xkoralsky.django_supervisor

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: django_channels_worker
           program_name: myapp_worker1
           only_channels: [ channel1 ]

License
-------

BSD
