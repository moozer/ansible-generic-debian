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
