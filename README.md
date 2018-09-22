# ansible-role-template

References:
[1] : http://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html

Openshidt origin singlenode
=========

This task aim to install Openshift Origin on a free CentOs/RHEL system. It will get all dependency before install the software

1- Create an service account for dependencies like docker
2- Deploy docker on the server if not installed
3- Manage proxy setting if needed (this part is the most sensible ... all best integrator of the place cannot do this ... unfortunatly it is a prerequisit of all company most of the time)


Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook Role Usage
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - {
              role: monrepos.rolename,
                    var1: 42,
                    Username: "testUser"
           }

Testing
----------------
To test the playbook locally, first install the required dependencies locally.

    $ ansible-galaxy install --role-file=./tasks/requirements.yml --roles-path=roles --force


License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).

Contributors
------------
