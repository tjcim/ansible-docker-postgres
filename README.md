ansible-docker-postgres
=======================

Installs PostgreSQL in a docker container with the default database postgres. Creates another database with user. Creates a .pgpass file and copies username/pass to /home/ubuntu/.profile

Requirements
------------

No requirements

Role Variables
--------------

Requires a dbname and dbuser variables. The playbook will create a corresponding database and user and grant all privs for the user on dbname.

Dependencies
------------

tjcim.ansible-vagrant-box
tjcim.ansible-docker

Example Playbook
----------------

    ---
    - hosts: pgadmin
      roles:
        - {role: 'ansible-docker-pgadmin', tags: 'pgadmin', dbname: 'testdb', dbuser: 'testuser'}

License
-------

BSD

Author Information
------------------

Connection Refused
