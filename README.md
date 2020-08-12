# Ansible Role: PostgreSQL

Role to install and configure [PostgreSQL](https://www.postgresql.org/).

## Requirements

Ansible 2.8 or later.

## Variables

### *postgresql_databases*

A list of databases to be created. The database owners will created
beforehand if necessary.

  postgresql_databases:
    - name: sympa
      owner: sympa
      password: nevairbe
    - name: rt4
      owner: requesttracker

#### Encoding

The encoding for a database is always `UTF-8`.

### *postgresql_extra_roles*

### *postgresql_dump_directory*

See "Dump databases" below.

## Dependencies

None.

## Dump databases

A separate task file `database-dump.yml` can be used to create database
dumps:

    - name: Dump database on source server
      import_role:
        name: postgresql
        tasks_from: database-dump.yml
      vars:
        postgresql_dump_directory: /var/cache/pgsql

## Configuration parameters

Configuration parameters can be set through the *postgresql_config_params*
variable.

Some of these required a restart of the PostgreSQL server, e.g:

  * wal_level
  * archive_command
  * max_wal_senders

## Example Playbook

Using *roles* keyword:

    - hosts: postgresql_servers
      roles:
        - { role: racke.postgresql }

Using tasks:

    - hosts: postgresql_servers
      tasks:
        import_role:
          name: racke.postgresql

## License

Artistic License 2.0

## Author Information

This role was created in 2020 by Stefan Hornburg (Racke).
