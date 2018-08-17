tripleo-f28-testbed
===================

Requirements
------------

1. You have a tenant account on an OpenStack cloud appropriate clouds.yaml
   configuration for the user executing the playbook.
   (e.g. ~/.config/openstack/clouds.yml)
2. Your OpenStack tenant has a private network (configurable) and one valid
   floating IP address already configured (set in config.yml)
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
