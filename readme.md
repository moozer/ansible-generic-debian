generic-debian
=================

this role replaces having single playbooks.

apt
---------

#### vars

   manage_apt: true

if the proxy var is not empty, it gets included in apt.conf
   apt_proxy_url: http://configserver01:9999

   apt_default_release: jessie
   apt_release: "{{ apt_default_release }}"
   apt_do_update_list: true
   apt_include_testing: false

Does upgrade of all packages, not recommended for normal use
Perhaps a candidate for --extra-vars
   apt_do_upgrades: false 

unattended-upgrades
----------------------

This enable a debian system to do automatic upgrade of certain packages.

Currently it is security updates that gets updated

#### vars

Disables of enables unattended upgrades

    enable_unattended_upgrade: true

