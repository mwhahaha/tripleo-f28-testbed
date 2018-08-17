provision-node
==============

Basic openstack node provisioning role.

Requirements
------------

Assumes clouds.yaml is used

Role Variables
--------------

``os_cloud`` - cloud name to use for authentication
``node_default_network`` - default network for the node (default: private)
``node_flavor`` - flavor of the node (default: m1.xlarge)
``node_image_container_format`` - glance image container format (default: bare)
``node_image_create`` - flag to enable/disable glance image upload (default: False)
``node_image_disk_format`` - glance image disk format (default: qcow2)
``node_image_download_location`` - image location download before upload to cloud (default: "{{ lookup('env','PWD') }}")
``node_image_name`` - glance image name to use (default: Fedora-Cloud-Base-28)
``node_image_source`` - source of the glance image to upload (default: "https://download.fedoraproject.org/pub/fedora/linux/releases/28/Cloud/x86_64/images/Fedora-Cloud-Base-28-1.1.x86_64.qcow2")
``node_nics`` - generic nic configuration for the node (default: [net-name=private])
``node_server_name`` - node name (default: node)
``node_ssh_user`` - ssh user to use (default: fedora)


License
-------

Apache-2.0

Author Information
------------------

Alex Schultz <aschultz@next-development.com>
