provision-node
==============

Basic openstack node provisioning role.

Requirements
------------

Assumes clouds.yaml is used

Role Variables
--------------

.. list-table:: Variables used for provision-node
   :widths: auto
   :header-rows: 1

   * - Name
     - Default Value
     - Description
   * - `os_cloud`
     - None
     - cloud name to use for authentication
   * - `node_default_network`
     - private
     - default network for the node
   * - `node_flavor`
     - m1.xlarge
     - flavor of the node
   * - `node_image_container_format`
     - bare
     - glance image container format
   * - `node_image_create`
     - False
     - flag to enable/disable glance image upload
   * - `node_image_disk_format`
     - qcow2
     - glance image disk format
   * - `node_image_download_location`
     - "{{ lookup('env','PWD') }}"
     - image location download before upload to cloud
   * - `node_image_name`
     - Fedora-Cloud-Base-28
     - glance image name to use
   * - `node_image_source`
     - "https://download.fedoraproject.org/pub/fedora/linux/releases/28/Cloud/x86_64/images/Fedora-Cloud-Base-28-1.1.x86_64.qcow2"
     - source of the glance image to upload
   * - `node_nics`
     - [net-name=private,net-name=provision]
     - generic nic configuration for the node
   * - `node_server_name`
     - node
     - node name
   * - `node_ssh_user`
     - fedora
     - ssh user to use

License
-------

Apache-2.0

Author Information
------------------

Alex Schultz <aschultz@next-development.com>
