# postgresql

This role installs and configures a PostgreSQL server.
It allows to set all configuration variables supported by PostgreSQL.

This role also makes PostgreSQL comply more to the FHS.
This is accomplished by moving configuration to /etc, logs to /var/log, and the databases to /var/db.

## Requirements

An apt- or pacman-based Linux distribution.

## Role Variables

This role seriously has a ton of variables.
Instead of copying the defaults file here, look it [up there](defaults/main.yml).
All variables from postgresql.conf are called exactly like they are called in the file.

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

CC-BY-SA

## Author Information

- [Janne Heß](https://github.com/dasJ)

