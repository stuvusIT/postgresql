# postgresql

This role installs and configures a PostgreSQL server.
It allows to set all configuration variables supported by PostgreSQL.

This role also makes PostgreSQL comply more to the FHS.
This is accomplished by moving configuration to /etc, logs to /var/log, and the databases to /var/lib.

## Requirements

Debian or Ubuntu

## Role Variables

This role seriously has a ton of variables.
Instead of copying the defaults file here, look it [up there](defaults/main.yml).
All variables from postgresql.conf are called exactly like they are called in the file but with `postgres_` prepended.

| Name                      | Default/Required        | Description                                                                              |
| ------------------------- | :---------------------: | ---------------------------------------------------------------------------------------- |
| `postgres_initdb`         | `initdb`                | Path to the initdb executable. On Ubuntu, the default value is automatically discovered. |
| `postgres_home_directory` | `/var/lib/postgresHome` | Path to the home of the postgres user                                                    |

## Dependencies

None

## Example Playbook

```yml
- hosts: postgres
  roles:
    - role: postgresql
      log_destination: []
      autovacuum: false
```

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](http://creativecommons.org/licenses/by-sa/4.0/).

## Author Information

- [Janne Heß](https://github.com/dasJ)

