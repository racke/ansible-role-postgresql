# Ansible Role: PostgreSQL

Role to install and configure [PostgreSQL](https://www.postgresql.org/).

## Requirements

Ansible 2.8 or later.

## Variables

### postgresql_databases

### postgresql_extra_roles

## Dependencies

None.

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

GPLv2

## Author Information

This role was created in 2020 by Stefan Hornburg (Racke).
