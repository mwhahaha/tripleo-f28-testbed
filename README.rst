tripleo-f28-testbed
===================

Requirements
------------

1. You have a tenant account on an OpenStack cloud appropriate clouds.yaml
   configuration for the user executing the playbook.
   (e.g. ~/.config/openstack/clouds.yml)
2. By default, the roles assume that your OpenStack tenant has two networks
   (private, provision) created (configurable) and one valid  floating IP
   address already configured (set in config.yml)
3. Ansible 2.4 or greater

How to run
----------

1. Modify config.yml

   a. Set the os_cloud to a valid clouds.yaml cloud name.
   b. Set the node_floating_ips to a valid floating ip pre-configured for your cloud.
   c. Update node_image_create to false if you do not wish to have the fedora
      image uploaded to your cloud by the playbook. See provision-node role for
      more options.
   d. Update node_image_download_location to a valid local path if you want the
      playbook to handle the fedora image uploading to your cloud (if node_image_create
      is True)

2. Run the following ansible-playbook

.. code-block::

    ansible-playbook provision.yml --extra-vars "@config.yml" --extra-vars "@tripleo-dlrn-data.yml"


Basic OpenStack tenant configurations
-------------------------------------

.. code-block::

    openstack keypair create default --public-key ~/.ssh/id_rsa.pub
    # needed to launch the instances for ovb
    openstack network create --internal private
    openstack subnet create private-net --subnet-range 192.168.100.0/24 --network private
    # needed for the 2nd interface for undercloud/standalone
    openstack network create --internal provision
    openstack subnet create provision-net --subnet-range 192.168.24.0/24 --network provision
    # need router for internets access/floating ips
    openstack router create internets
    openstack router set internets --external-gateway CHANGE_TO_YOUR_PUBLIC_NETWORK
    openstack router add subnet internets private-net
    # allow ssh/icmp
    openstack security group rule create --protocol tcp --dst-port 22:22 --remote-ip 0.0.0.0/0 default
    openstack security group rule create --protocol icmp default
    # create a floating ip
    openstack floating ip create CHANGE_TO_YOUR_FLOATING_IP_NETWORK
