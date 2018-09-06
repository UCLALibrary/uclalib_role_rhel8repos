uclalib_role_rhel7repos
=========

Ansible role that manages RHEL subscriptions and ensures the base set of RHEL7/CentOS7 yum repositories are enabled on the system.

If the host system is CentOS, subscription management is skipped.

If the host system is RHEL, you have option of attaching a Red Hat subscription using one of two methods:

1. Defining variables for `Organization ID` and `Activation Key`
2. Defining variables for `Username`, `Password`, `Pool ID`

RHEL7 repositories include:

* `rhel-7-server-rpms`
* `rhel-7-server-optional-rpms`
* `rhel-7-server-supplementary-rpms`
* `rhel-7-server-extras-rpms`

CentOS7 repositories include:
* `base`
* `updates`
* `extras`

Requirements
------------

You must have access to a valid Red Hat subscription account - options include:

* paid enterprise subscriptions
* free developer subscriptions

If you choose to use the **Activation Key** method:
* ensure the activation key is created within your account for your desired subscriptions
* reference: [Creating Red Hat Customer Port Activation Keys](https://red.ht/1TIdD2a)

If you choose to use the **Pool ID** method:
* ensure you know your Red Hat portal username/password
* reference: [Registration Assistant](https://red.ht/2wMB4ma)

Role Variables
--------------

Variables used when registering subscriptions via activation key:
* `rhel_org_id` - defines the organization ID associated with a Red Hat account

* `rhel_activation_key` - defines the activation key associated with your valid Red Hat subscription

Variables used when registering subscriptions via pool ids
* `rhel_username` - defines the username of Red Hat account with privileges to register hosts

* `rhel_password` - defines the password associated with username that has privileges to register hosts

* `rhel_pool_id` - defines the pool ID that is associated with a Red Hat subscription

Dependencies
------------

None.

Example Playbook
----------------

You'll want to define your subscription attachment variables within your playbook, group_vars, or host_vars.

A sample is provided below including variables using the activation key method within the playbook file:

    - hosts: servers
      vars:
        rhel_org_id: "123456"
        rhel_activation_key: "activation-key-string"
      roles:
         - { role: uclalib_role_rhel7repos }
