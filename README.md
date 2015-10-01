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
| `neutron_plugin_openvswitch_agent_local_ip` | `127.0.0.1` | GRE tunnels interface IP address. Enables GRE tunnelling if != `127.0.0.1` ||

### RabbitMQ (must exist)

| Name | Default value | Description | Note |
|---  |---  |---  |--- |
| `neutron_plugin_openvswitch_agent_rabbit_userid` | `rabbit_username_default` | RabbitMQ username for console auth ||
| `_rabbit_password` | `rabbit_pass_default` | RabbitMQ password for console auth ||
n_plugin_openvswitch_agent
| `neutron_plugin_openvswitch_agent_rabbit_virtual_host`| `/` | RabbitMQ virtual host for console auth ||
| `neutron_plugin_openvswitch_agent_rabbit_retry_interval` | `1` | Frequency to retry connecting to RabbitMQ ||
| `neutron_plugin_openvswitch_agent_rabbit_host` | `localhost` | The RabbitMQ broker address where a single node is used ||
| `neutron_plugin_openvswitch_agent_rabbit_port` | `5672` | The RabbitMQ broker port where a single node is used ||
| `neutron_plugin_openvswitch_agent_rabbit_hosts` | `$rabbit_host:$rabbit_port` | RabbitMQ HA cluster host:port pairs ||
| `neutron_plugin_openvswitch_agent_rabbit_ha_queues` | `False` | Use HA queues in RabbitMQ (x-ha-policy: all) ||

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

A complete Ansible playbook demo, which uses this role, is available on Github (openstack-ansible-galaxy/vagrant-ansible-openstack) <https://github.com/openstack-ansible-galaxy/vagrant-ansible-openstack>

---


License
-------

Apache

Author Information
------------------

Davide Guerri - davide.guerri@gmail.com
