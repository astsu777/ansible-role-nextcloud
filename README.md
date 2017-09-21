Ansible Role: NextCloud
=========

This role installs and configure NextCloud. Note that this particular role is depending on two others:
- [ansible-role-database](https://github.com/GSquad934/ansible-role-database)
- [ansible-role-webserver](https://github.com/GSquad934/ansible-role-webserver)


Once MariaDB and Nginx (from the two roles above) are up and running, this role performs the following actions:
- Download the latest version of NextCloud
- Create a system user and configure the database for the WebApp
- Configure and enables a Website in Nginx to access NextCloud
- Configure HTTPS and generate certificates with Let's Encrypt (if FQDN of the Website can be resolved)
- If FQDN of the Website cannot be resolved, default SSL certificates are deployed


Requirements
------------

No specific requirements for this role.

Role Variables
--------------

Multiple variables are necessary in order to properly configure NextCloud.

Here is how they can be configured:

```
nextcloud_user: nextcloud
nextcloud_password: MyPassword
nextcloud_db_password: MyPassword
nextcloud_hostname: nextcloud.mysite.com
certbot_email: mymail@mail.com
db_server: localhost
nextcloud_server: localhost
```

The variables above can be configured as group_vars or host_vars. As far as the credentials are concerned, these should be kept in a separate secret vars_file encrypted with *ansible-vault*.


Dependencies
------------

This role depends on two other roles as stated above:
- [ansible-role-database](https://github.com/GSquad934/ansible-role-database)
- [ansible-role-webserver](https://github.com/GSquad934/ansible-role-webserver)


If you install this role via Ansible-Galaxy, the name of the roles are [*GSquad934.database*](https://github.com/GSquad934/ansible-role-database) and [*GSquad934.webserver*](https://github.com/GSquad934/ansible-role-webserver).


However, if you have MariaDB and Nginx installed, this role should still works if you adapt it.

Example Playbook
----------------

Here is a simple example playbook to use this role:

```
hosts: nextcloud_srv
user: myuser
become: true
roles:
  - { role: nextcloud, tags: [ 'nextcloud' ] }
```

License
-------

MIT / BSD

Author Information
------------------

My name is Gaétan. You can follow me on [Twitter](https://twitter.com/gaetanict)

Website: [ICT Pour Tous](https://www.ictpourtous.com)
