uclalib_role_rhel7repos
=========

Ansible role to ensure the base set of RHEL7 yum repositories are enabled on the system.

Requirements
------------

The RHEL7 system must already be subscribed with Red Hat.

Role Variables
--------------

None.

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: uclalib_role_rhel7repos }
