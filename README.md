# postgresql

This role installs and configures a PostgreSQL server.
It allows to set all configuration variables supported by PostgreSQL.

This role also makes PostgreSQL comply more to the FHS.
This is accomplished by moving configuration to /etc, logs to /var/log, and the databases to /var/lib.

## Requirements

Debian 11 (Bullseye)

## Role Variables

This role seriously has a ton of variables.
Instead of copying the defaults file here, look it [up there](defaults/main.yml).
All variables from postgresql.conf are called exactly like they are called in the file but with `postgres_` prepended.

| Name                      |    Default/Required     | Description                                                                                                                                      |
| ------------------------- | :---------------------: | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| `postgres_initdb`         |        `initdb`         | Path to the initdb executable. On Ubuntu, the default value is automatically discovered.                                                         |
| `postgres_home_directory` | `/var/lib/postgresHome` | Path to the home of the postgres user                                                                                                            |
| `postgres_users`          |          `[]`           | List of dicts of [postgresql_user](https://docs.ansible.com/ansible/latest/collections/community/general/postgresql_user_module.html) parameters |
| `postgres_dbs`            |          `[]`           | List of dicts of [postgresql_db](https://docs.ansible.com/ansible/latest/collections/community/general/postgresql_db_module.html) parameters     |

### roles

| Name         | Default/Required | Description           |
| ------------ | :--------------: | --------------------- |
| `password`   |                  | The password to set   |
| `privileges` |                  | The privileges to set |

## Dependencies

None

## Example Playbook

```yml
- hosts: postgres
  roles:
    - role: postgresql
      postgres_users:
        - name: synapse
          password: TODO-change-me
      postgres_dbs:
        - name: synapse
          encoding: UTF8
          lc_collate: C
          lc_ctype: C
          template: template0
          owner: synapse

```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

## Author Information

- [Janne Heß](https://github.com/dasJ)

