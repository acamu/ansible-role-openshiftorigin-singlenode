# ansible-role-template

References:
[1] : http://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html

Openshift origin singlenode
=========

This task aim to install Openshift Origin on a free CentOs/RHEL system. It will get all dependencies before install the software

1- Create an service account for dependencies like docker
2- Deploy docker on the server if not installed
3- Manage proxy setting if needed (this part is the most sensible ... all best integrator of the place cannot do this ... unfortunatly it is a prerequisit of all company most of the time)


Requirements
------------

Extract of the DigitalOcean Website https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-ansible-on-centos-7

To get Ansible for CentOS 7, first ensure that the CentOS 7 EPEL repository is installed:

    sudo yum install epel-release

Once the repository is installed, install Ansible with yum:

    sudo yum install ansible

We now have all of the software required to administer our servers through Ansible.

Install the latest git package available in CentOS's repositories:

    sudo yum install git

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

and call the test file
    
    $ ansible-playbook -i hosts <your yaml> --tags "install" -vvv
    
    
Start cluster manually
----------------

    oc cluster up --env 'HTTP_PROXY=proxy.host' --env 'HTTPS_PROXY=proxy.host' --env '"NO_PROXY=10.128.0.0/14,172.30.0.0/16,192.1 68.0.0/16"'


Variable proxy
HTTP_PROXY
HTTPS_PROXY
NO_PROXY

    --http-proxy='': HTTP proxy to use for master and builds
    --https-proxy='': HTTPS proxy to use for master and builds
    --no-proxy=[]: List of hosts or subnets for which a proxy should not be used


Verify after launch that the cluster isgood configured

    $ docker exec -it origin bash
    echo $HTTP_PROXY
    echo $HTTPS_PROXY
    echo $NO_PROXY

If you want to know the other variables

    $ oc cluster up -h

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).

Contributors
------------

[1] : https://docs.okd.io/latest/install_config/build_defaults_overrides.html#manually-setting-global-build-defaults
