Ansible-Debian-PgBouncer
=========

This role installs and configures pgbouncer on Debian systems. It is tested on Ubuntu 14.04, but should work on any version for which pgbouncer is available via the default apt repositories.

Requirements
------------

none :-)

Role Variables
--------------

See `defaults/main.yml` for a complete list of variables. All vars are spelled the same as tehy are in pgbouncer.ini, and are prefixed with `pgbouncer`.
Special attention should be given to `pgbouncer_auth_users`

### pgbouncer_auth_users
This is a list of dict objects which each have a **name** and a *pass* property. You may use a plaintext or encrypted password. 
```yml
pgbouncer_auth_users:
  - name: postgres
    pass: pa55word
```
The above will result in a userlist.txt file that looks like this:
```
"postgres" "pa55word"
```

Dependencies
------------

If you are installing pgbouncer on a server other than your database server, you will also need to install **postgresql-client** if you want to query statistics. This role can do that for you if you set `pgbouner_install_pg_client` to true.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

MIT

More Information
----------------

I hope to combine this role with the [Redhat pgbouncer role](https://github.com/lesovsky/ansible-pgbouncer) very soon.
