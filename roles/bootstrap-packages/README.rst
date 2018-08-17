boostrap-packages
=================

This role is a stripped down version of the tripleo-quickstart-extra's
build-test-packages_.

.. _build-test-packages: http://git.openstack.org/cgit/openstack/tripleo-quickstart-extras/tree/roles/build-test-packages


Role Variables
--------------

``release`` - current relase to follow (default: master)
``build_repo_dir`` - workspace to use for the dlrn build (default: ansible_user_dir)
``dlrn_dlrn_repo_url`` - git repo for DLRN (default: https://github.com/openstack-packages/DLRN.git)
``dlrn_rdoinfo_repo_url`` - git repo for rdoinfo (default: https://github.com/redhat-openstack/rdoinfo)
``dlrn_target`` - target for dlrn configuration (default: fedora)
``dlrn_baseurl`` - base dlrn url to use (default: https://trunk.rdoproject.org/fedora/)
``dlrn_use_local_mirrors`` - use only local mirrors (default: false)
``dlrn_pre_installed`` - is dlrn pre installed (default: false)
``dlrn_skipped_projects`` - list of projects not to try and build (default: false)

``dlrn_change_list`` - list of project data to build

dlrn_change_list format:

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
