ansible
=======

Ansible playbooks

### Getting Started

Clone this repo and install requirements into a virtualenv:

    $ git clone git@github.com:WesleyCharlesBlake/ansible-provisioning.git
    $ mkvirtualenv ansible && workon ansible
    $ pip install -r requirements.pip

You will need to update your inventory to your actual hosts, as well as the munin/nagios configs in the `noc` role

### Examples

Uptime of all hosts:

    ansible --i=inventory/hosts aws-app -m shell -a "uptime" -o


Install / update htop:

    ansible aws-app -m apt -a "name=htop update_cache=yes" --sudo

Execute lsb_release on all hosts:

    ansible aws -m shell -a 'lsb_release -d' -o

Filtered fact:

    ansible all -m setup -a "filter=ansible_processor_*" -o


Run the NOC playbook:
   
    ansible-playbook --i=../inventory/hosts noc.yml -u root

Build with Packer (pakcer.io)

    packer validate base-ami.json
    packer build base-ami.json 

<!-- set: et ts=4 sts=4 tw= -->
