ansible-docker-postgres
=======================

Installs PostgreSQL in a docker container with the default database postgres. Creates another database with user. Creates a .pgpass file and copies username/pass to /home/ubuntu/.profile
 Adds http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg to sources (for postgresql v10)

* Adds to repo sources
* Installs postgresql-client
* Runs the alpine/postgres:latest container: https://hub.docker.com/_/postgres/
* Postgres is run with the default database named postgres and user postgres.
* The password for the postgres user will be created during initialization and will be placed in the `/home/ubuntu/.pgpass` file to enable passwordless connections from the vagrant guest.
* A second database is created using the variable `dbname`.
* A user is created with the name defined from `dbuser`.
* The password for the user will be created at initialization and will be placed in the `/home/ubuntu/.profile` file.
* A cronjob is created to backup the user database to `/home/ubuntu/pgsql_backups` every hour.

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
