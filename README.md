Neutron openvswitch agent plugin
=========

OpenStack Neutron openvswitch agent plugin installation

_Tested on Ubuntu Precise (12.04) and Trusty (14.04)_

Requirements
------------

None

Role Variables
--------------

### Neutron (set by this role)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `local_ip` | `127.0.0.1` | GRE tunnels interface IP address. Enables GRE tunnelling if != `127.0.0.1` ||


### RabbitMQ (must exist)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `rabbit_hostname` | `localhost` | Hostname/IP address where the RabbitMQ service runs ||
| `rabbit_username` | `rabbit_username_default` | RabbitMQ username for glance ||
| `rabbit_pass` | `rabbit_pass_default` | RabbitMQ password for glance. ||


Dependencies
------------

Neutron ml2 plugin role: `openstack-neutron_plugin_ml2`

Example Playbook
----------------

    - hosts: compute001
      roles:
        - role: openstack-neutron_openvswitch_agent
          local_ip: "{{ ansible_eth1.ipv4.address }}"

    - hosts: network001
      roles:
        - role: openstack-neutron_openvswitch_agent
          local_ip: "{{ ansible_eth1.ipv4.address }}"

---

A complete Ansible playbook demo, which uses this role, is available on Github (dguerri/vagrant-ansible-openstack) <https://github.com/dguerri/vagrant-ansible-openstack>

---


License
-------

Apache

Author Information
------------------

Davide Guerri - davide.guerri@gmail.com
