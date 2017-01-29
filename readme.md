generic-debian
=================

This role replaces having single playbooks for generic debian tasks.

See the [test](tests/) directory for minimal usage.

apt
---------

tasks to set up standard apt configuration and updates.

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

Disables or enables unattended upgrades

    enable_unattended_upgrade: true

ldap
-----------

Enable ldap lookups for users

#### vars

Disables or enables ldap use

  use_ldap: false

ldap server parameters

  ldap_uri: ldap://someldapserver
  ldap_basedc: dc=mydomain,dc=cm
  ldap_binddn:  cn=admin,dcmydomain,dc=com
  ldap_bindpw: somepassword
