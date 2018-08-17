bootstrap-packages
==================

This role is a stripped down version of the tripleo-quickstart-extra's
build-test-packages_.

.. _build-test-packages: http://git.openstack.org/cgit/openstack/tripleo-quickstart-extras/tree/roles/build-test-packages


Role Variables
--------------

.. list-table:: Variables used for bootstrap-packages
   :widths: auto
   :header-rows: 1

   * - Name
     - Default Value
     - Description
   * - `release`
     - master
     - current relase to follow
   * - `build_repo_dir`
     - ansible_user_dir
     - workspace to use for the dlrn build
   * - `dlrn_dlrn_repo_url`
     - https://github.com/openstack-packages/DLRN.git
     - git repo for DLRN
   * - `dlrn_rdoinfo_repo_url`
     - https://github.com/redhat-openstack/rdoinfo
     - git repo for rdoinfo
   * - `dlrn_target`
     - fedora
     - target for dlrn configuration
   * - `dlrn_baseurl`
     - https://trunk.rdoproject.org/fedora/
     - base dlrn url to use
   * - `dlrn_use_local_mirrors`
     - false
     - use only local mirrors
   * - `dlrn_pre_installed`
     - false
     - is dlrn pre installed
   * - `dlrn_skipped_projects`
     - false
     - list of projects not to try and build
   * - `dlrn_change_list`
     - []
     - list of project data to build

``dlrn_change_list`` format:

.. code-block::

    # just the code
    - host: "http://github.com"
      project: "openstack/tripleo-common"
      branch: "master"
      refspec: "master"
    # code with packaging
    - host: "http://github.com"
      project: "openstack/python-tripleoclient"
      branch: "master"
      refspec: "master"
      distgit:
        host: "http://github.com"
        project: "rdo-packages/tripleoclient-distgit"
        refpsec: "rpm-master"
    # just packaging, dlrn will figure out the code bits
    - host: ""
      distgit:
        host: "http://github.com"
        project: "rdo-packages/tripleoclient-distgit"
        refpsec: "rpm-master"

License
-------

Apache-2.0

Author Information
------------------

See original role for initial contributors

http://git.openstack.org/cgit/openstack/tripleo-quickstart-extras/tree/roles/build-test-packages

Additional updates done by Alex Schultz <aschultz@redhat.com>
