# Provision with Ansible over oVirt

Examples of how to provision a VM over oVirt with Ansible.


###Introduction

This documentation explains how to bring up a VM inside oVirt in a full automated way.
The Ansible 2.2 has some modules for oVirt which are permits create a VM inside a defined cluster, based over a pre-created template.
Also the oVirt modules uses the package cloud-init to setup the basics of the VM, such as hostname and networks.


###Requisites

- Ansible 2.2
- Access to an oVirt cluster with a full configurated datacenter, cluster and storage.
- A template VM (inside the datacenter to be used) with a OS and the following packages:
    - cloud-init
    - ovirt-guest-agent-common


###Using Ansible to provisiong over oVirt

Edit the file hosts_vars.yml according the needs of the service which is going to be provisioned.

Run the following command in order to provision the VM over oVirt:

```
$ ansible-playbook playbook.yml -e @hosts_vars.yml --ask-vault-pass
```
Note: The option `--ask-vault-pass` just is needed in case of the file ovirt_password.yml has been encrypted with ansible-vault, in this case the vault password is `123`.

###References

* http://www.ansible.com/how-ansible-works
* http://ovirt-ansible-modules.readthedocs.io/en/latest/_modules/ovirt_auth_module.html
* http://ovirt-ansible-modules.readthedocs.io/en/latest/_modules/ovirt_vms_module.html
* http://docs.ansible.com/ansible/add_host_module.html
* https://github.com/machacekondra/ovirt-ansible-example/wiki
