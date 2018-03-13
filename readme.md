generic-debian
=================

This role replaces having single playbooks for generic debian tasks.

See the [test](tests/) directory for example usage.

See variables with defaults in [defaults/main.yml](defaults/main.yml)

apt
---------

tasks to set up standard apt configuration and updates.

#### vars
```
generic_manage_apt: true
```

if the proxy var is not empty, it gets included in apt.conf

```
apt_proxy_url: http://someproxyserver:9999

apt_default_release: jessie
apt_do_update_list: true
apt_include_testing: false
```

smtp
--------------------

set up the debian box with mail capability to send mails to a smarthost

```
generic_manage_smtp: true
smtp_upstream: <upstream smarthost smtp server>
smtp_sender_fqdn: <domain/server name to use in mails>
```

unattended-upgrades
----------------------

This enable a debian system to do automatic upgrade of certain packages.

Currently it is security updates that gets updated

#### vars

Disables or enables unattended upgrades

```
generic_manage_unattended_upgrade: true
```


ldap
-----------

Enable ldap lookups for users

#### vars

Disables or enables ldap use

```
generic_manage_ldap: false
```

ldap server parameters

```
ldap_uri: ldap://someldapserver
ldap_basedc: dc=mydomain,dc=cm
ldap_binddn:  cn=admin,dcmydomain,dc=com
ldap_bindpw: somepassword
```

ssh daemon
---------------

This relates to configuring logging in to the host, not outgoing.

Basic config is very restrictive, and allows for specific named users to have other permissions. This uses the `Match user` option in sshd_config

#### vars

Enable/disable sshd config

```
generic_manage_sshd: true
```

Add users with special permission

```
sshd_users:
  - { username: "{{ansible_ssh_user}}", AllowTcpForwarding: "yes", PermitTTY: "yes" }
```

This is a list, and may be more than one entry. The options and the associated value is copied directly to the `sshd_config` file. Default is to disallow ttys and forwarding - ie. not very usefull. See `an sshd_config` for the list of options
